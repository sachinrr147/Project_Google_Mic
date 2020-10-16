<template>
  <div id="app">
     <div class="header">
      <p class="ma-2">Gmail</p>
      <p class="ma-2">Images</p>
      <img width="50" height="50" class="header__head-image"  alt="Vue logo" src="./assets/logo.png">
    </div>
    <div class="main">
       <v-row class="ma-0 pa-0" no-gutters>
          <v-col lg="6" md="6" sm="6" class="main__component">
       <img width="400" height="250" alt="Vue logo" src="https://www.newgadgets.de/uploads/2015/10/google_logo.jpg">

      <v-autocomplete
      v-model="model"
      :items="items"
      :loading="isLoading"
      chips
      clearable
      hide-details
      hide-selected
      item-text="name"
      item-value="symbol"
      label="Search for a coin..."
      solo
    >
      <template v-slot:no-data>
        <v-list-item>
          <v-list-item-title>
            Search for your favorite
            <strong>Cryptocurrency</strong>
          </v-list-item-title>
        </v-list-item>
      </template>
      <template v-slot:selection="{ attr, on, item, selected }">
        <v-chip
          v-bind="attr"
          :input-value="selected"
          color="blue-grey"
          class="white--text"
          v-on="on"
        >
          <v-icon left>
            mdi-bitcoin
          </v-icon>
          <span v-text="item.name"></span>
        </v-chip>
      </template>
    </v-autocomplete>
          </v-col>
       </v-row>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'App',
  data: () => ({
      isLoading: false,
      items: [
  {
    "id": "01coin",
    "symbol": "zoc",
    "name": "01coin"
  },
  {
    "id": "0-5x-long-algorand-token",
    "symbol": "algohalf",
    "name": "0.5X Long Algorand Token"
  },
  {
    "id": "0-5x-long-altcoin-index-token",
    "symbol": "althalf",
    "name": "0.5X Long Altcoin Index Token"
  },
  {
    "id": "0-5x-long-balancer-token",
    "symbol": "balhalf",
    "name": "0.5X Long Balancer Token"
  }],
      model: null,
      search: null,
      tab: null,
    }),
    watch: {
      model (val) {
        if (val != null) this.tab = 0
        else this.tab = null
      },
    },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  height: 100vh;
  width:100%
}
.header{
  display: flex;
  margin-left: 10px;
  justify-content: flex-end;
}
.header__head-image{
  border-radius: 50%;
}

.main {
  display: flex;
    flex-direction: column;
}
.main img {
  margin-left:25% ;
}
.main__component{
  margin: 0 auto ;
}
</style>
