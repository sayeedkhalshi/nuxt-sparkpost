<template>
  <h1 v-if="success">Mail Sent</h1>
  <form v-else id="form" ref="form" v-on:submit.prevent="submit">
    <input placeholder="Name" v-model="name" type="text" />
    <input placeholder="Email" v-model="email" type="email" />
    <input placeholder="Subject" v-model="subject" type="text" />
    <textarea placeholder="Message" v-model="message">Message</textarea>
    <button type="submit">Send Me An Email</button>

    <p>{{ message }}</p>
  </form>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      email: "",
      subject: "",
      message: "",
      success: false,
    };
  },

  methods: {
    submit() {
      fetch("http://ledwxnktvp.us08.fldrv.com/sendmail", {
        method: "POST",

        headers: {
          Accept: "application/json",
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          name: this.name,
          email: this.email,
          subject: this.subject,
          message: this.message,
        }),
      });

      this.success = true;
    },
  },
};
</script>
