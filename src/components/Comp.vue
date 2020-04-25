<template>
    <div class="col-md-12 full-screen-top" style="display: flex; flex-direction: row">
        <div class="col-md-4" style="padding-top: 5%">
            <p class="full-description">{{page.fields['description']}}</p>
        </div>
        <div class="col-md-4">
            <img src="../assets/banner1.png" style="width: 100%"/>
        </div>
    </div>
</template>

<script>
import { butter } from '@/buttercms'

export default {
  name: 'Comp',
  data() {
    return {
      page: {
        fields: {}
      }
    }
  },
  methods: {
    getPage() {
      butter.page.retrieve('*', 'portfolio')
        .then((res) => {
          this.page = res.data.data
          
        }).catch(() => {
        })
    },
    removeMobileMenu() {
      if(screen.width < 720)
        document.getElementsByClassName('navbar-toggler')[0].click()
    }
  },
  computed: {
    maillink: function() {
      return "mailto:" + this.page.fields['contact-email'];
    },
  },
  created() {
    this.getPage()
  }
}
</script>

<style scoped>

.full-description {
    color: black;
    float: right;
    margin-top: 5% !important;
    width:70% !important;
    font-size: 70% !important;
    line-height: 35px !important;
}
</style>