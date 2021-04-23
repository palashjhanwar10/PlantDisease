<template>
  <q-page class="bg-green-3">
    <div class="text-center constrain-more">
      <div class="q-pa-xl full-width text-center">
        <q-list separator bordered>
          <q-item v-for="plant in pal" :key="plant">
            <q-item-section
              ><q-btn flat @click="alert(plant.symptoms)" class="full-width"
                >{{ plant.name }}
              </q-btn></q-item-section
            >
          </q-item>
        </q-list>
      </div>
    </div>
  </q-page>
</template>

<script>
import plantdata from "../assets/data.json";
export default {
  data() {
    return {
      pal: plantdata
    };
  },
  methods: {
    alert(data) {
      var i, len, text;
      for (
        i = 0, len = data.length, text = '<ul class="text-subtitle1">';
        i < len;
        i++
      ) {
        text += "<li>" + data[i] + "</li>";
      }
      text += "</ul>";
      console.log("Text : - ", text);
      this.$q
        .dialog({
          title: "Treatment Details",
          message: text,
          html: true
        })
        .onOk(() => {});
    }
  }
};
</script>

<style lang="sass">
.constrain-more
  max-width: 700px
  margin: 0 auto
</style>
