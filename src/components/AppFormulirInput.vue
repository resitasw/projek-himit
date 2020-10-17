<template>
  <div :class="`opsi-formulir-${nama}`" class="opsi-formulir flex">
    <label :for="nama" v-if="showLabel">{{ label }}:</label>
    <input
        :placeholder="placeholder"
      :value="value"
      :type="tipe"
      :id="nama"
      class="margin-left"
      @input="ketikaNilaiBerubah"
    >
    <slot name="aksi"/>
    <slot name="aksi2"/>
  </div>
</template>

<script>
import { formulir } from '../mixins'

export default {
  name: 'AppFormulirInput',
  mixins: [formulir],
  props: {
    tipe: {
      type: String,
      default: 'text'
    },
    showLabel:{
        type: Boolean,
        default:true
    },
    placeholder:{
        type:String,
        default:'placeholder'
    }
  },
  methods: {
    ketikaNilaiBerubah(event) {
      if (this.tipe === 'number') {
        this.$emit('input', parseInt(event.target.value))
      } else {
        this.$emit('input', event.target.value)
      }
    }
  }
}
</script>
