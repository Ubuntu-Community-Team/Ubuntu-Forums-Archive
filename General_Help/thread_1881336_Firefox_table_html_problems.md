---
title: "Firefox table html problems"
date: 2011-11-15
forum: General Help
---

### Post by samjkdoman on 2011-11-15
My site is completly fine in windows+mac on all browsers i have tried, on ubuntu with chrome its fine but when i go on firefox my table goes really weird [IMG]https://mail.google.com/mail/?ui=2&ik=d400ee9635&view=att&th=133a6d9d1daa2211&attid=0.1&disp=emb&realattid=ii_133a6d99d6d7c912&zw[/IMG]

heres my css:
```
/* Site */
* {
margin: 0;
}
html, body {
height: 100%;
background-color:#3399FF;
}
.wrapper {
min-height: 100%;
height: auto !important;
margin: 0 auto -4em;
background-color:#3399FF;
font-family:Arial, Helvetica, sans-serif;
font-size:15px;
}
.header
{
margin-left:auto;
margin-right:auto;
background-color:#FFFFFF;
color:#3399FF;
padding-bottom:20px;
padding-top:20px;
}
.sea{
position:absolute;
}
.right{
position:absolute;
top:0px;
right:12px;
color:#3399FF;
top:12px;
}

table
{
position:absolute;
border-collapse:collapse;
border:5px solid #FFFFFF;
color:#FFFFFF;
border-bottom:0px;
border-right:0px;
border-left:0px;
border-top:0px;
z-index:2;

}
th
{
position:inherit;
border-collapse:collapse;
border:5px solid #FFFFFF;
color:#FFFFFF;
z-index:2;
border-top:0px;
}
td
{
position:inherit;
border-collapse:collapse;
border:5px solid #FFFFFF;
color:#FFFFFF;
z-index:2;
border-top:0px;
}
.text{
position:relative;
top:100px;
color:#FFFFFF;
width:80%;
left:18%;
font-size:18px;
z-index:3;
margin-bottom:22%;

}
.map
{position:absolute;
right:0px;
color:#FFFFFF;
top:12px;
z-index:6;
}
a, href
{color:#FFFFFF;
 text-decoration:  none;
}

.footer, .push {
position:relative;
z-index:5;
}

```

and my html 

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
"http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<title>Site</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">

        <link rel="stylesheet" href="judy.css" ... />
    </head>
    <body>
        <div class="wrapper">
		<div class="sea"><img src="the1.png" align="left" width="150px" height="80px">
		</div>
	    <div class="header" align="center"><h1>Judy Renihan.<p>Psychotherapy Counselling</p></h1>
	
		  </div>
			<div class="right" align="center">
			<strong>Call to book an appointment<p></p> 01323 895594</strong>
			</div>
			<table width="100%" valign="top" width=183 style='table-layout:fixed'>

<tr>
<th bgcolor="#3399FF" border="5" bordercolor="#ffffff" align="left" ><font color="#ffffFF"><h3>Feelings of loneliness </font></th>
<th><h3> <a href="index.html">Home</a></th>
<th><h3><a href="fees.html">Fees</a></th>
<th><h3><a href="location.html">Location</a></th>
<th><h3>Testimonials</th>
<th><h3><a href="TRANSACTIONAL.html">Transactional Analysis</a></th>
</tr>
<tr>
<td><h3>Relationship Problems</td>
</tr>
<tr>
<td><h3>Bereavement</td>
</tr>
<tr>
<td><h3>Stress</td>
</tr>
<tr>
<td><h3>Anxiety</td>
</tr>
<tr>
<td><h3>Trauma</td>
</tr>
<tr>
<td><h3>Work/Career Issues</td>
</tr>
<tr>
<td><h3>Addictions</td>
</tr>
<tr>
<td><h3>Low self worth</td>
</tr>
<tr>
<td><h3>Anger management</td>
</tr>
<tr>
<td><h3>Depression</td>
</tr>
<tr>
<td><h3>Abuse</td>
</tr>
</h4>
</table>
<font color="#FFFFFF">
<div class="text">
<strong>
Sometimes we can face difficulties in our lives that impact on our work, relationships and how we manage our daily lives. I believe that, with help, people can find the inner strength to make changes that can benefit and enhance their lives. This change can be realised through an empathetic relationship with a therapist in a safe space where the client can discuss freely their feelings in confidence.
<p>&nbsp;</p>
I have been trained in both counselling and psychotherapy and have worked with clients of all ages and from many different backgrounds in both the NHS and private sector.
<p>&nbsp;</p>

I believe that effective results can only be reached if there is an understanding relationship between therapist and client and for that reason I invite prospective clients to come for an initial half hour consultation for which there is no charge and no obligation.
<p>&nbsp;</p>

I can offer help with, anxiety, depression, relationship problems, bereavement, stress, anger management, trauma counselling, abuse issues (sexual and physical), self harming behaviour, addictions and self esteem issues.
</div>			

			
			
			
			
			
            <div class="push"></div>
        </div>
        <div class="footer" align="center">
            <p>Judy Renihan. Psychotherapy Counselling Copyright (c) 2011</p>
        </div>
    </body>
</html>
<body>
</body>
</html>

```

i have tried every thing can some one please help!
([http://www.e30webdesign.com/](http://www.e30webdesign.com/))

---

### Post by vasa1 on 2011-11-15
It displays decently with Aurora (~Firefox 10)

---

