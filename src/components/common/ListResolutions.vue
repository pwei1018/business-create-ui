<template>
  <div
    v-if="resolutionList.length > 0"
    id="list-resolutions"
  >
    <v-divider class="mx-4" />
    <article class="pa-4">
      <v-row no-gutters>
        <v-col
          cols="12"
          sm="3"
          class="pr-4"
        >
          <label
            id="resolution-label"
          >Resolution or Court Order Dates</label>
        </v-col>
        <v-col
          cols="12"
          sm="9"
        >
          <p>
            Dates of resolution or court orders to change the company's share structure. This includes dates for
            adjusting the special rights or restrictions on a specific class or series of shares:
          </p>
        </v-col>
      </v-row>
      <v-row no-gutters>
        <v-col
          cols="12"
          sm="3"
          class="pr-4"
        />
        <v-col
          cols="12"
          sm="9"
        >
          <div id="resolution-list">
            <tr
              v-for="(item, index) in resolutionList"
              :key="index"
            >
              <td class="font-weight-bold">
                {{ item.date }}
              </td>
            </tr>
          </div>
        </v-col>
      </v-row>
    </article>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import { useStore } from '@/store/store'
import { Getter } from 'pinia-class'
import { ResolutionIF } from '@/interfaces'

@Component({})
export default class ListResolutions extends Vue {
  @Getter(useStore) getResolutions!: ResolutionIF[]

  get resolutionList (): ResolutionIF[] {
    return this.getResolutions
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/styles/theme.scss';

#list-resolutions {
  font-size: $px-14;
  color: $gray7;

  p {
    font-size: $px-14;
  }
}

label {
  font-weight: bold;
  color: $gray9;
}

</style>
