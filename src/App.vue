<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col-md-12">
        <h1>Personas</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-md-12">
        <formulario-persona @add-persona="agregarPersona" />
        <tabla-personas
          :people="people"
          @delete-persona="eliminarPersonas"
          @actualizar-persona="actualizarPersona"
        />
      </div>
    </div>
  </div>
</template>

<script>
// El '@' es el directorio 'src'
import FormularioPersona from "@/components/FormularioPersona.vue";
import TablaPersonas from "@/components/TablaPersonas.vue";

export default {
  name: "App",
  components: {
    TablaPersonas,
    FormularioPersona,
  },
  data() {
    return {
      people: [
        {
          id: 1,
          nombre: "Jon",
          apellido: "Nieve",
          email: "jon@email.com",
        },
        {
          id: 2,
          nombre: "Tyrion",
          apellido: "Lannister",
          email: "tyrion@email.com",
        },
        {
          id: 3,
          nombre: "Daenerys",
          apellido: "Targaryen",
          email: "daenerys@email.com",
        },
      ],
    };
  },
  methods: {
    agregarPersona(persona) {
      let id = 0;

      if (this.people.length > 0) {
        id = this.people[this.people.length - 1].id + 1;
      }

      this.people = [...this.people, { id, ...persona }];
    },

    eliminarPersonas(id) {
      this.people = this.people.filter((persona) => persona.id !== id);
    },

    actualizarPersona(id, personaActualizada) {
      this.people = this.people.map((persona) =>
        persona.id === id ? personaActualizada : persona
      );
    },
  },
};
</script>

<style>
button {
  background: #009435;
  border: 1px solid #009435;
}
</style>
