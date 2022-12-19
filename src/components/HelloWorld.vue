<script setup>
import axios from 'axios'
import { onBeforeMount, reactive } from 'vue';

let items = reactive({});

let testArray =reactive([]);
let testObject =reactive({});


console.log(items);
console.log(testObject);
console.log(testArray)
onBeforeMount (() => {
  testArray.values = [1,2,3];
  testObject.values = {
    item: 1,
    itemt: 2
  }

  const path = 'http://localhost:8888/items'
      axios.get(path)
        .then(response => {
       
          items.values = response.data;
      
        })
        .catch(error => {
          console.log(error)
        });
        
})

</script>

<template>
  <div>
    <li v-for="item in testObject" :key="item.id">
      {{ item }}
      
    </li>
    <li v-for="item in testArray" :key="item.id">
      {{ item }}
      
    </li>
    <li v-for="item in items" :key="item.id">
      {{ item }}
      
    </li>
  </div>
</template>