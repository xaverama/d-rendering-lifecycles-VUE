<template>
  <h1>Dynamic & Conditional Rendering, Lifecycle Hooks</h1>
  <div class="container">
    <div v-if="myRectangles?.length < 6">
      <div v-for="item in myRectangles">
        <div :style="{ height: item.height + 'px', width: item.width + 'px', background:item.color}"> {{item.color}}</div>
      </div>
    </div>
  </div>

</template>

<script setup lang="ts">
import {onMounted, ref} from "vue";
import {dataService, Rectangle} from "./services/data-service";



const data = dataService();

const myRectangles = ref<Rectangle[]>()


onMounted(async () => {
  myRectangles.value = await data.getAllData()
})

</script>

<style scoped>
.container{
  display: flex;
  gap: 1rem;
}
div {
  display: flex;
}


</style>
