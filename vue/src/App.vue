<template>
  <div>
      <router-view/>    
      

  </div>
</template>

<script>
import {
    mapState,
    mapActions
} from "vuex"
export default {
  name: 'App',
  computed: {
        ...mapState({
            idUser: state => state.Auth.user.id,
        })
    },
  mounted(){
    this.confirmAuthenticated()
  },
  methods: {      
      ...mapActions([
            'confirmAuthenticated',
      ]),  
        loginRedirect() {
            if (!this.idUser) {
                this.$router.push({
                    name: 'home'
                })
            }
        }
    },
     watch: {
        idUser() {
            this.loginRedirect()
        }
    }
};
</script>
