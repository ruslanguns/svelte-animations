<script>
  import { fly } from "svelte/transition";
  import { quintOut } from "svelte/easing";
  let myTransition = {
    delay: 250,
    duration: 300,
    x: 100,
    y: 500,
    opacity: 0.5,
    easing: quintOut,
  };

  let open = true;
  $: toggle = () => (open = !open);
</script>

<button on:click={toggle}> Toggle edit panel</button>

<div class="contedor-general">
  <div class="contenedor-tabla">
    <div class="tabla">table</div>

    <div class="paginador">pagination</div>
  </div>
  {#if open}
    <div transition:fly={myTransition} class="edit">edit</div>
  {/if}
</div>

<style>
  .contedor-general {
    display: flex;
    margin: 0 10em;
  }

  .contenedor-tabla {
    flex: 2;
  }

  .tabla {
    background-color: red;
    height: 300px;
    text-align: right;
    padding: 1em;
  }

  .paginador {
    background-color: lightblue;
    height: 50px;
  }

  .edit {
    background-color: orange;
    height: 350px;
    flex: 1;
    padding: 1em;
  }

  @media (max-width: 600px) {
    .contedor-general {
      margin: 0 1em;
    }
</style>
