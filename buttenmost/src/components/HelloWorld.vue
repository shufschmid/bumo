<template>
  <v-container>
    <v-row class="text-center">
      <v-parallax src="../src/assets/titelbild.jpg" height="450">
        <v-col cols="12">
          <v-card>
            Buttenmost aus Hochwald
            <h4 class="subheading white--text" v-show="!isSaison">
              Die Buttenmost-Saison 2021 ist vorbei. Frischen Buttenmost gibt es
              wieder ab September 2022.
              <span
                @click="$vuetify.goTo('#onlineshop', goToOptions)"
                style="text-decoration: underline"
                >jetzt vorbestellen</span
              >
            </h4>
            <h4 class="subheading white--text" v-show="isSaison">
              Es gibt wieder frischen Buttenmost -
              <span
                @click="$vuetify.goTo('#onlineshop', goToOptions)"
                style="text-decoration: underline"
                >jetzt bestellen</span
              >
            </h4>
          </v-card>
        </v-col>
      </v-parallax>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "HelloWorld",

  data() {
    return {
      saisonstart: "2022-09-13",
    };
  },
  computed: {
    heute: function () {
      //today = new Date();
      //for testing during season
      //today = new Date("2021-09-21");
      return new Date();
      //for testing during Season
      //return new Date("2021-09-18");
    },
    saisonstartDate: function () {
      return new Date(this.saisonstart);
    },
    saisonstartString: function () {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return this.saisonstartDate.toLocaleDateString("de-DE", options);
    },
    isSaison: function () {
      if (this.heute - this.saisonstartDate > 0) {
        return true;
      } else {
        return false;
      }
    },
  },
});
</script>
