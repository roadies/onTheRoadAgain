<template>
<div>
  <b-col>
    <b-card :title="title" :img-src="imageLink" img-alt="Image" img-top tag="journal" style="max-width: 200rem" class="mb-2" :footer="dayDate">
      <b-card-text>
        {{ body }}
      </b-card-text>
      <b-button v-on:click="deleteJournal(id)" variant="danger">delete</b-button>
    </b-card>
  </b-col>
</div>
</template>

<script>
import axios from "axios";
export default {
  props: ["title", "date", "body", "imageLink", "id"],
  data(){
    return {
      dayDate: dayjs(this.date).format('DD/MM/YYYY')
    }
  },
  methods: {
    deleteJournal(id) {
      axios
        .delete(`/api/journal/${id}`)
        .then(() => this.$el.parentNode.removeChild(this.$el));
    },
  },
};
</script>

<style scoped>
</style>
