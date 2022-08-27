<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>This works</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Blank</ion-title>
        </ion-toolbar>
      </ion-header>
    
      <div class="container">

        <button @click="register">Register Test</button>

      </div>

      <div class="container">
        <button>Login Test</button>
      </div>

    </ion-content>
  </ion-page>
</template>

<script>
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar } from '@ionic/vue';
import { defineComponent } from 'vue';
import axios from "axios";

export default defineComponent({
  name: 'HomePage',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
  },
  data() {
    return {
      csfr: ''
    }
  },
  mounted() {
  },
  methods: {
    async register() {
      axios.defaults.withCredentials = true;

      await axios.get('http://mobile-app-backend.test/sanctum/csrf-cookie')
      await axios.post("http://mobile-app-backend.test/register", {
        username: "test@test.com",
        password: "password"
      })
          .then((response) => {
            console.log(response)
          })
          .catch((error) => {
            console.log(error)
          })
    }
  }

});
</script>

