<template>
  <div class="container">
    <div class="row">
      <div class="col-md-4">
        <div class="card">
          <div class="card-body">
            <h5 class="card-title">{{ currentJoke.setup }}</h5>
            <p class="card-text">{{ currentJoke.punchline }}</p>
            <div class="text-center mt-4">
              <button class="btn btn-primary" @click="getJoke">Reload</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentJoke: {}
    };
  },
  mounted() {
    this.getJoke();
  },
  methods: {
    getJoke() {
      fetch('https://official-joke-api.appspot.com/random_joke')
        .then(response => response.json())
        .then(data => {
          this.currentJoke = data;
        })
        .catch(error => {
          console.error(error);
        });
    }
  }
};
</script>

<style>
.container {
  margin-top: 50px;
}
</style>
