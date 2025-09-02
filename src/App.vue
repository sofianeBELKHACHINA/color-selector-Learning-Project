<script setup>
import colorsList from './assets/data/colorsList.json'
import { ref } from 'vue'

const selectedColor = ref('rgb(245, 245, 245)')
const selectColor = (color) => {
  selectedColor.value = color
}
</script>

<template>
  <main>
    <h1>Sélectionnez une couleur</h1>
    <div>
      <section>
        <div>
          <div v-for="subColorsList in colorsList" :key="subColorsList[0]">
            <div
              v-for="color in subColorsList"
              :key="color"
              :style="{ background: color }"
              @click="selectColor(color)"
              :class="{
                selected: color === selectedColor,
              }"
            ></div>
          </div>
        </div>
      </section>
      <section>
        <div>
          <p>{{ selectedColor }}</p>
          <div class="selectedColor"></div>
        </div>
      </section>
    </div>
  </main>
</template>

<style scoped>
main {
  padding: 50px;
  display: flex;
  flex-direction: column;
  height: 100vh;
  background-color: white;
}

main > div {
  /* border: 1px solid black; */
  display: flex;
  flex: 1;
  justify-content: center;
  align-items: center;
  gap: 20px;
}

section {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

section > div {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

section > div > div {
  display: flex;
  gap: 10px;
}

div > div > div {
  border: 1px solid black;
  width: 30px;
  height: 30px;
  border-radius: 3px;
}

h1 {
  font-size: 45px;
  font-weight: bold;
  text-align: center;
  margin-bottom: 30px;
}
.selectedColor {
  border: 1px solid black;
  border-radius: 30px;
  height: 200px;
  width: 200px;
  background-color: v-bind(selectedColor);
}

p {
  text-align: center;
  margin-bottom: 20px;
}

.selected {
  box-shadow: 0px 0px 10px black;
}
</style>
