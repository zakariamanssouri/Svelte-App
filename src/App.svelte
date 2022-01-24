<script>
  export let name;
  export let movies = new Array();
  import { onMount } from "svelte";

  onMount(() => {
    getMovies();
  });

  function getMovies() {
    movies = fetch("http://localhost:3000/movies", {
      method: "GET",
    })
      .then(function (response) {
        console.log(response.status + " status");
        response.json().then(function (data) {
          console.log(data);
        });
      })
      .catch(function (err) {
        console.log("Fetch Error :-S", err);
      });
  }
</script>

<main>
  <h1 class="bg-light">Hello {name}!</h1>
  <p>
    Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
    how to build Svelte apps.
  </p>

  <table>
    <th>title</th>
    <th>genres</th>
    <th>year</th>
  </table>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  /*h1 {
    color: #ff7300;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }*/

  table {
    padding: 10px;
    background-color: #eee;
  }
  th  {
    padding: 10px;
    margin: 10px;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
