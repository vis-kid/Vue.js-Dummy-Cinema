<template>
<div id="movie-list">
  <h2>Movie List</h2>
  <div v-for="movie in filteredMovies" class="movie">{{ movie.title }}</div> 
</div>
</template>

<script>
  import genres from "../util/genres";

  export default {

  data: function() {
       return {
         movies: [
           { title: "Home Alone", genre: genres.COMEDY },
           { title: "Mesmer", genre: genres.DRAMA },
           { title: "Die Hard", genre: genres.CRIME}
         ] 
       }
     },

     props: [ 'genre', 'time'],
     methods: {
       moviePassesGenreFilter(movie) {
         if (!this.genre.length) {
           return true;
         } else {
           return this.genre.find(genre => movie.genre === genre);
         }
       }
     },

     computed: {
       filteredMovies() {
         return this.movies.filter(this.moviePassesGenreFilter); 
       } 
     }
   }
</script>
