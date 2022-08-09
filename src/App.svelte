<script lang="ts">
import Formulario from "./componets/Formulario.svelte";
import Titulo from "./componets/Titulo.svelte";
import Usuario from "./componets/Usuario.svelte";

 
  import type IUsuario from "./interfaces/IUsuario";

  let usuario: IUsuario | null = null;

  function definirUsuario(evento: CustomEvent<IUsuario | null>) {
    usuario = evento.detail;
    
  }
</script>

<div class="app">
  <header>
    <Titulo />

    <div class="busca-usuario">
      <Formulario on:aoAlterarUsuario={definirUsuario} />
    </div>
  </header>

  {#if usuario}
    <Usuario {usuario} />
  {/if}
</div>

<style>
  .app {
    max-height: 100vh;
  }

  header {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .busca-usuario {
    position: relative;
    width: 70%;
  }
</style>