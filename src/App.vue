<template>
    <div class="container">
      <section class="min-vh-100 d-flex align-items-center justify-content-center">
        <div class="container">
          <div class="row">
            <div class="col-12 d-flex flex-column align-items-center justify-content-center">
              <div class="card mb-3 p-3">
                <div class="card-body">
                  <div class="pt-4 pb-4">
                    <h5 class="card-title text-center pb-0 fs-4">🤸 Beshy App 🤸</h5>
                  </div>
                  <div class="row g-3">
                    <div class="col-12 mb-1">
                      <div class="input-group">
                        <input v-model="inputText" type="text" class="form-control" placeholder="Type here Beshy..." />
                        <button @click="clearInput" class="btn border trash">
                          <i class="bi bi-trash"></i>
                        </button>
                      </div>
                    </div>
                    <div class="col-12">
                    <button class="btn btn-primary w-100 generate" @click="generate">
                      Generate Beshy &nbsp;
                      <i class="bi bi-arrow-right"></i>
                    </button>
                  </div>
                  </div>
                  <div v-if="showResult" class="col-12" id="output">
                    <div class="output-text">{{ beshiefiedText }}</div>
                    <div>
                      <button @click="copyResult" class="btn copy" title="Copy">
                        <i class="bi bi-files"></i>
                      </button>
                    </div>
                  </div>
                  <div class="col-12">
                    <p class="text-success text-center p-2">{{ status }}</p>
                  </div>
                  <div class="mt-5">
                    <hr />
                    <div class="col-12 mt-4 d-flex justify-content-center">
                      <p>
                        Developed by:
                        <a href="https://kent.jdchost.com" target="_blank">Kent</a>
                      </p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
</template>

<script>
export default {
  data() {
    return {
      inputText: "",
      status: "",
      beshiefiedText: "",
      showResult: false,
    };
  },
  methods: {
    generate() {
      if (this.inputText !== "") {
        this.beshiefiedText = this.inputText.replaceAll(" ", "🤸");
        this.showResult = true;
        this.status = "";
      } else {
        this.showResult = false;
        this.status = "No text has been inputted Beshy.";
      }
    },
    copyResult() {
      this.status = "Text has been copied. Share it now, Beshy ko!";
      const elem = document.createElement("input");
      document.body.appendChild(elem);
      elem.value = this.beshiefiedText;
      elem.select();
      document.execCommand("copy");
      document.body.removeChild(elem);
    },
    clearInput() {
      this.inputText = "";
      this.showResult = false;
      this.status = "";
    },
  },
};
</script>

<style>

body {
  font-family: Nunito;
  background-color: #fff;
}

h5 {
  color: #09496e;
}

.generate {
  background-color: #09496e;
  border: 1px solid #09496e;
}

#output {
  display: flex;
  justify-content: space-between;
  margin-top: 15px;
  background-color: #0d6dfd11;
  border-radius: 7px;
}

#output .output-text {
  padding: 8px;
  width: 100%;
  color: #09496e;
}

.trash {
  border-radius: 0 7px 7px 0 !important;
}

.trash:hover {
  color: #09496e;
}

#app {
  grid-template-columns: 1fr !important;
}

p {
  color: #929292;
}

a {
  color: #313131;
}

.copy:hover {
  color: #09496e;
}

hr {
  color: #09496e;
}

</style>
