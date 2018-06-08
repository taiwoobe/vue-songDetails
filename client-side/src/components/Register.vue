<template>
    <div class="">
    <div class="container-fluid">
        <div class="row">
            <div class="headerBackground">
                <h3 style="padding-top: 25px;"> {{ msg }}</h3>
            </div>
        </div>
    </div>
    <div class="loginSection">
        <div class="container">
            <div class="">
                <div class="col-md-3">
                </div>
                <div class="col-md-6 loginForm">
                    <form @submit.prevent="register">
                        <label for="email"> Email Address:</label>
                        <input type="text" required class="form-control" placeholder="Enter Email Address" v-model="email">
                        <br>
                        <label for="password"> Password:</label>
                        <input type="password" required class="form-control" placeholder="Enter Password" v-model="password">
                        <br>
                        <div class="spinner-holder">
                            <button class="btn btn-primary">Register</button>
                            <div class="spinner-class" v-if="loading">
                                <Spinner name="wave" color="chocolate" :noFadeIn="fader"/>
                            </div>
                        </div>
                    </form>
                </div>
                <div class="col-md-3">
                </div>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
import authentication from '../configurations/authentication'
export default {
  data () {
    return {
      msg: 'Registration Page',
      fader: true,
      loading: false,
      email: '',
      password: ''
    }
  },
  methods: {
    async register() {
    this.loading = true;
    const response = await authentication.register({
        email: this.email,
        password: this.password
    })
    console.log(response.data)
    this.email =''
    this.password = ''
    this.loading = false;
    }
  }
}
</script>

<style scoped>
.headerBackground {
  height: 80px;
  background: chocolate;
  color: white;
  text-align: center;
  margin-top: -20px;
  margin-bottom: 20px;
}
.loginSection {
  margin-top: 120px;
}
.loginForm {
  border: 1px solid #1f030321;
  padding: 30px;
  border-radius: 5px;
  box-shadow: 0 0 35px rgba(0, 0, 0, 0.2);
}
label {
  color: rgb(134, 131, 131);
  margin-bottom: 10px;
}
.btn-primary {
    padding: 8px 40px;
    background: chocolate;
    border: chocolate;
}
.btn-primary:hover {
    background: chocolate;
    border: chocolate;
}
.btn-primary:active {
    background: chocolate;
    border: chocolate;
    outline: none;
}
.spinner-class {
  display: inline-block;
  padding-top: 10px;
  margin-left: 40px;
}
.spinner-holder {
  display: flex;
  align-items: center;
}
</style>
