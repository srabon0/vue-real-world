<template>
  <div class="events">
    <EventCard :event="event" :key="event.id" v-for="event in events" />
  </div>
</template>

<script>
// @ is an alias to /src

import EventCard from '@/components/EventCard.vue'
import EventServices from '@/services/EventServices.js'
export default {
  name: 'HomeView',
  components: {
    EventCard
  },
  data () {
    return {
      events: null
    }
  },
  created () {
    EventServices.getEvents()
      .then(response => {
        this.events = response.data
      })
      .catch(error => {
        console.log(error)
      })
  }
}
</script>

<style scoped>
.events{
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
