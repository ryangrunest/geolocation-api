<script>
export default {
  name: 'HomeView',
  data() {
    return {
      lat: '',
      lng: ''
    }
  },
  methods: {
    onGeolocationError(err) {
      console.warn(`ERROR: ${err.code}: ${err.message}`);
    },
    onGeolocationSuccess(pos) {
      console.log('got cords', pos);

      this.lat = pos.coords.latitude;
      this.lng = pos.coords.longitude;
    },
    requestGeolocation() {
      console.log('adf')
      navigator.geolocation.getCurrentPosition(this.onGeolocationSuccess, this.onGeolocationError)
        
    },
  },
  mounted() {
    this.requestGeolocation();
  }
}
</script>

<script setup lang="ts">
</script>

<template>
  <main>
    <p>lat: {{lat}}</p>
    <p>long: {{lng}}</p>
    <button @click="requestGeolocation">request geolocation</button>
  </main>
</template>
