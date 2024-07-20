<template>
  <img class="logo" alt="Vue logo" src="../assets/logo.jpg" />
  <h1>sign up</h1>
  <div class="form">
    <input type="text" placeholder="username" />
    <input type="text" placeholder="email" />
    <input type="text" placeholder="password" />
    <button type="submit">sign up</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "SignUp",
  data() {
    return {
      form: {
        username: "",
        email: "",
        password: "",
      },
      error: null,
    };
  },
  methods: {
    async submitForm() {
      this.error = null;
      try {
        const response = await axios.post(
          "http://localhost:5000/signup",
          this.form
        );
        console.log("Sign up successful", response.data);
      } catch (error) {
        this.error = error.response
          ? error.response.data.message
          : "An error occurred";
      }
    },
  },
};
</script>

<style scoped>
.logo {
  width: 250px;
}
.form input {
  width: 300px;
  height: 30px;
  padding-left: 20px;
  padding-bottom: 20px;
  display: block;
  margin-bottom: 40px;
  margin-right: auto;
  margin-left: auto;
  border-radius: 1px solid black;
}

.form button {
  width: 320px;
  height: 40px;
  border-radius: 5px;
  background-color: #2c3e50;
  color: white;
}
</style>
