---
title: "html tag woes"
date: 2006-06-08
forum: General Help
---

### Post by RajivNair on 2006-06-08
hi everyone,

is anything wrong with the tags in this file :-

"<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/1999/REC-html401-19991224/loose.dtd">
<html>
<head>
<title>Cstrike MOTD</title>
<style type="text/css">
pre 	{
		font-family:Verdana,Tahoma;
		color:#FFB000;
    	}
body	{
		background:#000000;
		margin-left:8px;
		margin-top:0px;
		}
a	{
    	text-decoration:    underline;
	}
a:link  {
    color:  #FFFFFF;
    }
a:visited   {
    color:  #FFFFFF;
    }
a:active    {
    color:  #FFFFFF;
    }
a:hover {
    color:  #FFFFFF;
    text-decoration:    underline;
    }
</style>
</head>
<body scroll="yes">
<pre>
You are playing Condition Zero on SANPADA LAN
<b>ADMINISTRATOR
Siddharth Menon</b>
We expect all to play clean game..
Here you get to kill your bad friends (ONLINE).
COME ONLINE EVERYDAY FROM 9:30-1100PM TO PLAY MULTIPLAYER

<b>Counter Strike Community Sanpada (CSCS)</b>
For futher updates please vist the LAN based web page
<a href="http://10.12.42.136">http://siddlonghorn/</a>
If you don't have an access there contact the ADMINISTRATOR

Visit the official Condition Zero web site @
<a href="http://www.cs-conditionzero.com">www.cs-conditionzero.com/</a>
</pre>
</body>
</html>
"

if no then why isnt wine able to read it and 
if yes how to read it in wine.

---

### Post by Jussi Kukkonen on 2006-06-08
How should wine read it? Do you want it rendered on IE or what do you mean?

Can't help with IE, I don't use it. The code itself is fine -- except for the "scroll=yes" attribute, which is IE-only and useless (since the default is yes). Another style nitpick would be using the same color for visited and  non-visited links, that's just user-unfriendly.

---

### Post by TrinitronX on 2006-06-08
if you need to validate HTML code, here's the internet standard for doing so (for future reference):
[http://validator.w3.org/](http://validator.w3.org/)

---

### Post by compmodder26 on 2006-06-08
As mentioned previously, wine does absolutely nothing for html.  Wine is an emulator for MS Windows programs.  You need a web browser to render html (or a wysiwyg editor, but that is another matter).  Perhaps you can clarify what you meant for us so we can better help you.

---

