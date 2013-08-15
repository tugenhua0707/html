                                                        html
====

                                                  html css常见的布局
一： 如何用css实现"等高布局"。
     
     有时候为了让网页实现美观，在不知道高度的情况下，我们要用css实现等高布局效果，传统的方法，我们可以用javascript实现，但是
  由于需求决定或者其他的情况下，我们只能用css实现，其方法主要是采用“隐藏容器溢出”、"正内补丁"和"负外补丁"结合的方法实现的.
  代码如下：
  
      <div id="wrap">
        <div id="left">
                <p>left</p>
                <p>left</p>
                <p>left</p>
                <p>left</p>
                <p>left</p>
        </div>
        <div id="center">
                <p>center</p>
                ……（20个或更多个）
                <p>center</p>
        </div>
        <div id="right">
                <p>right</p>
                <p>right</p>
                <p>right</p>
        </div>
    </div>
    
    css样式如下：
    
<style>
	* {
        margin:0;
        padding:0;
  }
  #wrap {
          overflow:hidden;
          width:1000px;
          margin:0 auto;
  }
  #left, #center, #right {
          margin-bottom:-10000px;
          padding-bottom:10000px;
  }
  #left {
          float:left;
          width:250px;
          background:#00FFFF;
  }
  #center {
          float:left;
          width:500px;
          background:#FF0000;
  }
  #right {
          float:right;
          width:250px;
          background:#00FF00;
  }
</style>

其中的 10000px 可以修改为其他值，但不能小于最高列的高度。 经测试，此方法兼容 IE6/IE7/IE8 beta 2/FF/Opera/Chrome 。 
方法很简单吧。从这里可以看出：看似简单的 CSS,其实并不简单。

  其实还有一种方法：是用表格实现，具体的可以研究下表格。
  

二： 如何使左侧固定宽度右侧自适应。
     
     HTML代码如下：
     
     <div id="box">
	      <div id="right">right right</div>
	      <div id="left">left</div>
	      <div style="clear:both"></div>
    </div> 
    
    css代码如下：
    
    <style>
      *{ padding:0; margin:0; font-size:12px; line-height:1.8; font-family:Verdana;}
      #box{ background:#FFCC00;border-left:200px solid #FF9900;}
      #left{margin-left:-200px; width:200px; /*position:static;*/}
      #right{float:right; width:100%}
   </style> 
