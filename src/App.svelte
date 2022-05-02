<script>
  import data from "./foods.json";
  const foods = data.foods;
  console.log(foods[0]);
  console.log(foods[0].name);

  let searchedItems = [];

  const handleChange = (event) => {
    let searchInput = event.target.value;
    if (searchInput !== "") {
      searchedItems = foods.filter((item) =>
      item.name.toLowerCase().includes(searchInput.toLowerCase())
    )
    } else { searchedItems = []}

    console.log(searchedItems);
  };
</script>

<main>
  <div class="container">
    <input
      on:input={handleChange}
      placeholder="What do you want to eat?"
    />
    <ul>
      {#each searchedItems as { name, price, tags }}
        <li><a href="#">{name}</a><span>{price}$</span></li>
      {/each}
    </ul>
  </div>
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  }
  :global(html, body) {
    margin: 0;
    padding: 0;
    border: none;
    height: 100%;
  }

  ul {
    list-style: none;
    padding: 0;
    gap: 5px;
    display: flex;
    flex-direction: column;
    gap: 1em;
    margin-top: 2em;
  }

  main {
    padding: 1em;
    position: absolute;
    min-height: 100%;
    min-width: 100%;
    display: flex;
    text-align: center;
    align-items: center;
    background-image: url("https://365psd.com/images/istock/previews/9068/90688657-food-seamless-pattern-elements-and-background.jpg");
    background-size: contain;
    background-repeat: repeat;
  }
  .container {
    display: flex;
    flex-direction: column;
    margin: auto;
    background-color: rgba(58, 58, 58, 0.2);
    border-radius: 2em;
    backdrop-filter: blur(8px);
    border: 5px #1f1f1f;
    padding: 2em;
  }
  
  input {
    color: #1f1f1f;
    font-size: 2rem;
    padding: 0.4em;
    border-radius: 0.5em;
    margin: auto;
    border: none;
  }

  li {
    text-align: left;
    padding-left: 1em;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  li span {
    font-weight: 600;
    color: tomato;
  }
  a {
    text-decoration:  none;
    color: blueviolet;
    font-size: 1.5em;
  }

  input:hover,
  input:focus {
    background-color: rgba(203, 203, 203, 0.4);
  }
</style>
