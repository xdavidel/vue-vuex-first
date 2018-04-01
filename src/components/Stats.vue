<template>
  <div class="stats">
    <h1>A different component</h1>
    <p>There are currently {{ countLinks }} links</p>

    <button v-on:click="removeAllLinks">Remove All Links</button>
    <p>{{msg}}</p>
  </div>
</template>

<script>
import { mapGetters, mapMutations, mapActions } from "vuex";

export default {
  name: "Stats",
  data() {
    return {
      msg: ""
    };
  },
  methods: {
    ...mapMutations(["REMOVE_ALL"]),
    ...mapActions(["removeAll"]),
    removeAllLinks() {
      this.removeAll().then(() => {
        this.msg = "All links has been removed";
        setTimeout(() => {
          this.msg = "";
        }, 1500);
      });
    }
  },
  computed: {
    ...mapGetters(["countLinks"])
  }
};
</script>

<style scoped>
button {
  padding: 10px;
  margin-top: 30px;
  width: 100%;
  background: none;
  border: 1px solid lightgray;
  outline: 0;
  cursor: pointer;
}
</style>
