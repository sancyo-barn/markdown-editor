<template>
  <div>
    <div class="container toggle-container">
      <div class="toggle">
        <button v-on:click="setToggleStatus()">write</button>
        <button v-on:click="setToggleStatus()">preview</button>
      </div>
    </div>
    <div class="container markdown-container">
      <div class="markdown-editor" v-bind:style="setEditorStyle()">
        <div class="markdown-write">
          <h2 class="notice">Write</h2>
        </div>
        <div class="markdown-preview">
          <h2 class="notice">Preview</h2>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isToggleActive: true,
      styleWriteActive: {
        transform: "translateY(0)"
      },
      stylePreviewActive: {
        transform: "translateX(-50%)"
      }
    };
  },
  methods: {
    setToggleStatus() {
      this.isToggleActive = !this.isToggleActive;
    },
    setEditorStyle() {
      if (this.isToggleActive) {
        return this.styleWriteActive;
      } else if (!this.isToggleActive) {
        return this.stylePreviewActive;
      }
    }
  }
};
</script>

<style>
.container {
  max-width: 1100px;
  position: relative;
  overflow: hidden;
}
.toggle-container {
  margin: 3rem auto 0 auto;
}
.markdown-container {
  margin: 0 auto 3rem auto;
}
.markdown-editor {
  display: flex;
  width: 200%;
  transform: translateX(-50%);
  transition: 0.3s;
  background: #fff;
}
.markdown-write {
  height: 200px;
  background: #fff;
  width: 100%;
  padding: 0.8rem;
}
.markdown-preview {
  width: 100%;
  background: #fff;
  height: 200px;
  padding: 0.8rem;
}
</style>
