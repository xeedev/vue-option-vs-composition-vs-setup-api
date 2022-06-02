<template>
  <div class="about">
    <p>Information: {{ info }}</p>
    <button @click="test()">Change Text</button>
    <strong>{{ fullName }}</strong>
  </div>
</template>
<script>
// only add (setup) if you want to use 3rd setup api
// 1: Options API
/*export default {
  data: () => ({
    info: "Again",
    firstName: "Zeeshan",
    lastName: "Ahmad",
  }),
  computed: {
    fullName() {
      return this.firstName + " " + this.lastName;
    },
  },
  methods: {
    test() {
      this.firstName = "zeemax";
      this.lastName = ".";
    },
  },
};*/
// 2: Composition API
/*import { defineComponent, ref, computed } from "vue";
export default defineComponent({
  setup() {
    const info = "Again";
    const firstName = ref("Zeeshan");
    const lastName = ref("Ahmad");
    const fullName = computed(() => firstName.value + " " + lastName.value);
    function test() {
      firstName.value = "zeemax";
      lastName.value = ".";
    }
    return { fullName, info, test };
  },
});*/
// 3: Setup API (preffered) please add "setup" keyword in above script for this
/*import { ref, computed } from "vue";
const info = "Again";
const firstName = ref("Zeeshan");
const lastName = ref("Ahmad");
const fullName = computed(() => firstName.value + " " + lastName.value);
function test() {
  firstName.value = "zeemax";
  lastName.value = ".";
}*/
// 4: Hybrid approach for v2 to v3 migration
// you cant use data attributes inside setup
import { defineComponent, ref, computed } from "vue";
export default defineComponent({
  data: () => ({ info: "Again" }),
  setup() {
    const firstName = ref("Zeeshan");
    const lastName = ref("Ahmad");
    const fullName = computed(() => firstName.value + " " + lastName.value);
    function test() {
      firstName.value = "zeemax";
      lastName.value = ".";
    }
    return { fullName, test };
  },
});
</script>
