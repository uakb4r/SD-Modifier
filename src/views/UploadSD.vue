<template>
  <div>
    <h1>Service Definition Modifier</h1>
    <h2>Please upload your service definition file below</h2>
    <div class="fileUploadDiv" style="cursor: pointer">
      <md-field>
        <label>Click to Upload a File</label>
        <md-file @md-change="onFileUpload($event)" />
      </md-field>
    </div>
    <p style="color: red;">{{errMsg}}</p>
  </div>
</template>

<script>
  export default {
    date() {
      return {
        errMsg: ''
      }
    },
    methods: {
      onFileUpload(evt) {
        const file = evt[0];
        const _fileRead = new FileReader();
        _fileRead.onload = ((e) => {
          // console.log(e.target.result);
          this.isValidJSON(e.target.result);

        });
        _fileRead.readAsText(file);
        // this.file = evet[0]
      },
      isValidJSON(obj) {
        try {
          return(JSON.parse(obj))
        } catch {
          this.errMsg = "Is NOT valid JSON!"
          return false
        }
      }
    }
  }
</script>

<style scoped>
  .fileUploadDiv {
    width: 500px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid grey;
  }
</style>