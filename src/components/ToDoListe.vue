<template>
  <div class="col" v-for="ToDoListe in ToDoListe" :key="ToDoListe.id">
    <div class="card text-center">
      <div class="card-header">
        To-Do-Liste
      </div>
      <div class="card-body">
        <h5 class="card-title">{{ToDoListe.headline}}</h5>
        <p class="card-text">{{ToDoListe.note}}</p>
        <a href="#" class="btn btn-primary">erstelle Eintrag</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ToDoListe',
  data () {
    return {
      ToDoListe: []
    }
  },
  mounted () {
    const requestOptions = {
      method: 'GET',
      redirect: 'follow'
    }
    fetch('https://localhost:8080/entity/ToDoListeEntity', requestOptions)
      .then(response => response.json())
      .then(result => result.forEach(ToDoListe => {
        this.ToDoListe.push(ToDoListe)
      }))
      .catch(error => console.log('error', error))
  }
}
</script>

<style scoped>

</style>
