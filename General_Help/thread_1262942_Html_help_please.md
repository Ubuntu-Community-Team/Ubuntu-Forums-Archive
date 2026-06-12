---
title: "Html help please"
date: 2009-09-10
forum: General Help
---

### Post by angelln on 2009-09-10
Hi All

I need some help with the following html coding:
[COLOR="Blue"][COLOR="Blue"]
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<!-- MagicComment: MVTimeout -->

<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Untangle Login</title>
<script type="text/javascript">if (top.location!=location) top.location.href=document.location.href;</script>
<style type="text/css">
/* <![CDATA[ */
@import url(/images/base.css);
/* ]]> */
</style>
</head>
<body>
<div id="main" style="width: 500px; margin: 50px auto 0 auto;">
 <div class="main-top-left"></div><div class="main-top-right"></div><div class="main-mid-left"><div class="main-mid-right"><div class="main-mid">
 <!-- Content Start -->

      <center>
        <img alt="" src="/images/BrandingLogo.gif" /><br />

        <b></b><br/>

        Untangle Login

        <div style="margin: 0 auto; width: 250px; padding: 40px 0 5px;">

        <form method="post" action=[COLOR="Red"]"/auth/login?url=/setup/welcome.do&amp;realm=Administrator"[/COLOR]>
          <table><tbody>
            <tr><td style="text-align:right">Server:</td><td><em>&nbsp;localhost</em></td></tr>
            <tr><td style="text-align:right">Username:</td><td><input id="username" type="text" name="username" value="admin"/></td></tr>
            <tr><td style="text-align:right">Password:</td><td><input id="password" type="password" name="password" /></td></tr>
          </tbody></table>
          <br />
          <div style="text-align: center;"><button value="login" type="submit">Login</button></div>
        </form>

        <script type="text/javascript">document.getElementById('password').focus();</script>

        </div>
      </center>


 <!-- Content End -->
 </div></div></div><div class="main-bot-left"></div><div class="main-bot-right"></div>
 <!-- Box End -->
</div>
</body>
</html>[/COLOR][/COLOR]

What I need to know is how can I change the title. I cant seem to find the file contaning the html coding that i posted above. the way I found this coding was 'right clicked the web page and clicked on view source'
The code that I marked in red seems to be the "file"(welcome.do) that contains this code, but i cant seem to find the file. 

Please, any help will be appreciated 

Best regards

---

### Post by plade on 2009-09-10
I don't understand what exactly you want.

---

### Post by NoaHall on 2009-09-10
<title>Untangle Login</title>
Change here.

---

### Post by wojox on 2009-09-10
[http://www.innove.com.ph/auth/login?url=/setup/welcome.do&realm=Administrator](http://www.innove.com.ph/auth/login?url=/setup/welcome.do&realm=Administrator)

Is this your Website?

What it's doing is posting back to a php script to validate who you are.

---

### Post by angelln on 2009-09-11
I want to change the title:
<title>Untangle</>:(

---

### Post by NoaHall on 2009-09-11
I still don't get it, but here's what I think you want

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<!-- MagicComment: MVTimeout -->

<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Untangle</title>
<script type="text/javascript">if (top.location!=location) top.location.href=document.location.href;</script>
<style type="text/css">
/* <![CDATA[ */
@import url(/images/base.css);
/* ]]> */
</style>
</head>
<body>
<div id="main" style="width: 500px; margin: 50px auto 0 auto;">
<div class="main-top-left"></div><div class="main-top-right"></div><div class="main-mid-left"><div class="main-mid-right"><div class="main-mid">
<!-- Content Start -->

<center>
<img alt="" src="/images/BrandingLogo.gif" /><br />

<b></b><br/>

Untangle Login

<div style="margin: 0 auto; width: 250px; padding: 40px 0 5px;">

<form method="post" action="/auth/login?url=/setup/welcome.do&amp;realm=Administrator">
<table><tbody>
<tr><td style="text-align:right">Server:</td><td><em>&nbsp;localhost</em></td></tr>
<tr><td style="text-align:right">Username:</td><td><input id="username" type="text" name="username" value="admin"/></td></tr>
<tr><td style="text-align:right">Password:</td><td><input id="password" type="password" name="password" /></td></tr>
</tbody></table>
<br />
<div style="text-align: center;"><button value="login" type="submit">Login</button></div>
</form>

<script type="text/javascript">document.getElementById('password').fo cus();</script>

</div>
</center>


<!-- Content End -->
</div></div></div><div class="main-bot-left"></div><div class="main-bot-right"></div>
<!-- Box End -->
</div>
</body>
</html>

---

### Post by gordintoronto on 2009-09-11
> **angelln said:**
> I need some help with the following html coding:

<head>
<title>Untangle Login</title>
<script type="text/javascript">if (top.location!=location) top.location.href=document.location.href;</script>
<style type="text/css">
/* <![CDATA[ */
@import url(/images/base.css);
/* ]]> */
</style>
</head>

What I need to know is how can I change the title. I cant seem to find the file contaning the html coding that i posted above. the way I found this coding was 'right clicked the web page and clicked on view source'
The code that I marked in red seems to be the "file"(welcome.do) that contains this code, but i cant seem to find the file. 

Please, any help will be appreciated 

Best regards

Do you have FTP access to the web site where this comes from?  Start at index.html and figure out where it's going.

Alternatively, grab all the html or php from the web site and search for the file containing "Untangle Login".

---

### Post by Maheriano on 2009-09-11
> **NoaHall said:**
> <title>Untangle Login</title>
Change here.

This is what you want to do, it should be located in the index.html file. Or whichever page you want to change it on.

---

### Post by Codix121 on 2009-09-11
Dude it's right there:
<title>***THIS RIGHT HERE WILL BE YOUR TITLE***</title>

Not to be rude but this is one of those "DUH" questions...

---

### Post by Irvine_himself on 2009-09-11
This is somebody delusional dreaming about being a hacker!

I just checked out some things:

[http://www.innove.com/](http://www.innove.com/)
[http://en.wikipedia.org/wiki/Globe_Telecom](http://en.wikipedia.org/wiki/Globe_Telecom)
[http://www.who.is/whois/innove.com/](http://www.who.is/whois/innove.com/)
[http://www.google.co.uk/search?q=Innove%20LLC&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.co.uk/search?q=Innove%20LLC&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by NoaHall on 2009-09-11
Wait, so this guy was trying to hack a military website BY CHANGING THE TITLE? I'm pretty sure nobody could be that stupid...


Note to Admins - only calling the OP stupid if he was indeed trying to hack a military website via changing the title (which he didn't even know how to do)

---

### Post by Irvine_himself on 2009-09-11
I cant' think of any other explanation, I mean can you really see a company with that kind of pedigree showing such a complete lack of knowledge about server sided scripting. Even more frightening is the thought that such a company would have to ask advice on a public forum.

---

