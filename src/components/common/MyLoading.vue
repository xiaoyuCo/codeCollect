<template>
  <div
    v-if="showLoading"
    class="loading-wrap"
    :style="{top: top + 'px'}"
  >
    <span class="loading-text">{{ text }}</span>
    <icon-font
      class="icon-font"
      name="loading3"
    />
  </div>
</template>

<script>
import IconFont from '@/plugin/icon/IconFont'
export default {
  name: 'MyLoading',
  data () {
    return {
      showLoading: false,
      text: '',
      top: '50'
    }
  },
  components: {
    IconFont
  },
  methods: {
    show ({ msg = '加载中' } = {}) {
      this.text = msg
      this.showLoading = true
    },
    close () {
      this.showLoading = false
      if (typeof this.onClose === 'function') {
        this.onClose(this)
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.loading-wrap {
  @extend %fix;
  width: 240px;
  height: 36px;
  border-radius: 4px;
  left: 50%;
  transform: translateX(-50%);
  background-color: rgba(0, 0, 0, 0.4);
  @extend %flex-c;
}
.loading-text {
  font-size: 0.4rem;
  margin-right: 8px;
  color: #fff;
}
.icon-font {
  animation: rotate infinite 1s linear;
  color: #fff;
  font-size: 0.5rem;
}
</style>
