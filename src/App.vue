<template>
  <div id="app">
<div class="styleEditor">
    <pre>
     {{code}}
    </pre> 
   <div v-html="styleCode"></div>
   </div>
  
   
   <div class="resumeEditor">
    <div v-if="enableHtml" v-html="result"></div>
    <pre v-else>{{result}}</pre>
  </div>
   
    
   
  

   
  </div>
   

</template>

<script>


export default {
  name: 'app',
  components: {
  
  },
  data(){
  return{
    code:``,
    finalCode: 
    `/*
    * Inspired by http://strml.net/
    * 大家好，我是思敏君 
    * 金秋九月，很多公司都在招聘
    * 这里我也来写一份简历了！
    */
     
    /*首先给所有的元素加上过渡效果*/
    *{
      transition:all .3s;
    }
    /*当然白色的背景还是单调了一点，来点背景看看*/
    html{
      color:rgb(222,222,222);background:rgb(0,43,54);
    }
    /*文字离边框似乎有点近了，我们加点距离看看*/
    .styleEditor{
      padding:.5em;
      border:1px solid;
      margin:.5em;
      overflow:auto;
      width:45vw;
      height:60vw;
    }
    /*代码高亮*/
    .token.selector{color:rgb(133,153,0);}
    .token.property{color:rgb(187,137,0);}
    .token.function{color:rgb(42,162,152);}
     
    /*再来加一点酷炫的3D效果吧*/
    html{
     perspective:1000px;
    }
    .styleEditor{
     position:fixed;left:0;top:0;
     -webkit-transition:none;
     transition:none;
     -webkit-transform:rotateY(10deg)translateZ(-100px);
             transform:rotateY(10deg)translateZ(-100px);
     }
     /* 接下来我给自己准备一个编辑器 */
     .resumeEditor{
     position: fixed;
     right:10px; 
     top: 0;
     padding: .5em;  
     margin: .5em;
     width: 48vw; height: 90vh;
     border: 1px solid;
     background: white; color: #222;
     overflow: auto;
    }
   
   .resumeEditor{
  padding: 2em;
}
.resumeEditor h2{
  display: inline-block;
  border-bottom: 1px solid;
  margin: 1em 0 .5em;
}
.resumeEditor ul,.resumeEditor ol{
  list-style: none;
}
.resumeEditor ul> li::before{
  content: '•';
  margin-right: .5em;
}
.resumeEditor ol {
  counter-reset: section;
}


    
    `,
        currentMarkdown: '',
        fullMarkdown: `方应杭
jjjjjj
        
  `}

  },
  created(){
  var n=0;
  setInterval(()=>{
  this.code=this.finalCode.substring(0,n)
  n+=1
  },10)
},
  computed:{
  highlightedCode: function () {
        return Prism.highlight(this.code, Prism.languages.css)
      },
  styleCode:function(){
  return '<style>'+this.code +'</style>'
  
  }
  }


}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
html{
  min-height:100vh;
}
*{
  box-sizing:border-box;
}
</style>
