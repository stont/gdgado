<template>
    <v-container class="pa-0 my-0">
        <v-layout wrap align-center justify-center row fill-height class="mt-2 elevation-2 white" style="border:1px solid #e0e0e0;border-radius:5px">
            <v-flex xs12 sm4 md3 lg3 class="pa-4" >
                <v-img
                    :src="getImgUrl(letterDetails.Image)"
                    :lazy-src="getImgUrl(letterDetails.Image)"
                    width="100%">
                    <v-layout
                        slot="placeholder"
                        fill-height
                        align-center
                        justify-center
                        ma-0
                    >
                        <v-progress-circular indeterminate color="grey lighten-5"></v-progress-circular>
                    </v-layout>
                </v-img>
            </v-flex>
           <v-flex xs12 sm8 md9 lg9 class="pa-2 py-4 px-3" >
                <p class="google-font mb-0" style="font-size:150%;color:rgb(2, 119, 189)">{{letterDetails.Name}}</p>
                 <span class="google-font mt-1 mb-0 grey--text"  style="font-size:105%">
                    <v-icon small>book</v-icon>
                    {{letterDetails.Pages}} Pages
                </span>  
               <p class="google-font mt-2 mb-1" style="font-size:115%;color:#757575">
                   {{letterDetails.Description}}
               </p>
                
                <v-btn color="#1a73e8" v-if="letterDetails.DownloadLink.length>0" :href="letterDetails.DownloadLink" target="_blank" class="ma-0 elevation-0 my-2" dark style="text-transform: capitalize;border-radius:5px;"> 
                    Read Now
                </v-btn>
                &nbsp;
            
            </v-flex> 
        </v-layout>

    </v-container>
</template>

<script>
import letterDetails from '@/assets/data/newsLetter.json'
export default {
    components:{
    },
    data() {
        return {
            letterDetails:letterDetails
        }
    },
    created(){
        
    },
    methods:{
        getImgUrl(pic) {
            if(pic.length>0){
                return require('@/assets/img/'+pic)
            }else{
                return require('@/assets/img/featureEvent/imagenotfound.png')
            }
        },
    },
    filters:{
        summery: (val,num)=>{
            return val.substring(0,num)+".."
        },
        dateFilter: (value)=>{
            const date = new Date(value)
            return date.toLocaleString(['en-US'], {month: 'short', day: '2-digit', year: 'numeric'})
        }
    }
}
</script>
