---
title: "Auto-login for hotspot service"
date: 2011-05-01
forum: General Help
---

### Post by oldmankit on 2011-05-01
Hello,

My apartment management recently installed a new system so that I have to log-in every time I want to use the internet (wifi).  It's kinda annoying because for some reason firefox doesn't offer to remember my username and password for this site.  It's more annoying because when it opens  a new window which has to be kept open while I use the internet, and after login redirects me to google.co.th, which I don't ever use.

Is there a script I could create which will login for me and handle this annoyance?  It would make my daily life on computers just that little bit nicer.

Many thanks,
Kit

---

### Post by oldmankit on 2011-05-03
bump bump

---

### Post by Cheesehead on 2011-05-03
Look at the web page source code. HTML submit? Or (more likely) Javascript?

Write a script to download the page upon starting a network connection, run the JS, reply to the prompts, undo the redirect, and pretend to keep the window open...all without actually opening a window. You can do it in Bash or Python or Javascript or other languages.

It's a bit of homework for you.
Might be worthwhile.

Do remember to share what you learn!

---

### Post by oldmankit on 2011-05-09
> **Cheesehead said:**
> Look at the web page source code. HTML submit? Or (more likely) Javascript?

Write a script to download the page upon starting a network connection, run the JS, reply to the prompts, undo the redirect, and pretend to keep the window open...all without actually opening a window. You can do it in Bash or Python or Javascript or other languages.

It's a bit of homework for you.
Might be worthwhile.

Do remember to share what you learn!


Hi,

Thanks for the cool advice. 

This is beyond me; I'm just an interested  home user without any skills in java, or python, or even writing anything more than the most banal bash scripts you can imagine.  I looked at the logon page source and pulled out the stuff that looks useful:
```

<script language="JavaScript">

function MM_openBrWindow(theURL,winName,features) { //v2.0
 var t =  window.open(theURL,winName,features);
t.focus();
}

function atlogin_domain(atdomain) {
if (document.login.UserName.value.indexOf('@') == -1) {
atboxs = document.login.UserName.value + "@" + atdomain;
document.login.UserName.value = atboxs;
}
}
</script>
```And then a bunch of stuff which contains the fields to enter username/password:

```
<TD style="BACKGROUND-COLOR: #000000" width=117><INPUT name=UserName id="UserName" AUTOCOMPLETE="OFF"></TD>
...
<TD style="BACKGROUND-COLOR: #000000"><INPUT name=Password type="password" id="Password" AUTOCOMPLETE="OFF" Onkeyup="atlogin_domain('Saithong');"></TD>

```Well, now I see why firefox doesn't offer to remember username/pwd.  
A bit of hidden stuff at the end of the page:
```

          <INPUT TYPE="HIDDEN" NAME="chal" VALUE="d59199872df928162b9895f119dbf9d1">
          <INPUT TYPE="HIDDEN" NAME="uamip" VALUE="192.168.182.1">

          <INPUT TYPE="HIDDEN" NAME="uamport" VALUE="3990">
          <INPUT TYPE="HIDDEN" NAME="userurl" VALUE="">
          <INPUT TYPE="HIDDEN" NAME="mac" VALUE="this has my mac address in">
          <INPUT TYPE="HIDDEN" NAME="nasid" VALUE="Saithong">

```And a last little bit of java:
```
<script language="JavaScript">
<!--
if (document.login) {
document.login.UserName.focus();
}
// -->
</script>

```If anyone can help me make the next step, that'd be great, but no worries if not.

---

### Post by oldmankit on 2011-05-09
PS: There is no key on the wireless connection now, and network-manager connects to it automatically.

---

