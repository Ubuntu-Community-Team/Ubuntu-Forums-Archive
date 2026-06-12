---
title: "Wine to run IExplorer and get on the net."
date: 2009-10-16
forum: General Help
---

### Post by Hopalong on 2009-10-16
I've installed WINE. I select it, choose 'Browse C:/ drive', click 'programfolder', click 'internet explorer', click 'iexplorer.exe@. I get a blank panel headed 'Wine Internet Explorer'. How do I access the net from here? - or should I be doing something quite different?
  I've got Vista dual booted, if that helps (but hasn't Wine got its own IE?).:confused:

---

### Post by mike555 on 2009-10-16
Any reason your not using Firefox? it comes with Ubuntu and is much safer than IE.

---

### Post by 314 on 2009-10-16
not too mention you can also use chrome aswell i find it more user friendly then firefox but it is soooo much better then IE

[http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux](http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux)

its in alpha but it runs really fast

---

### Post by Hopalong on 2009-10-18
I know, I know: but my bank won't let me connect through to other deposits with Firefox, as it does with Explorer. Presumably it uses Explorer to make the connection? Change banks? - no, I like this one, and I've been with it for ever!

---

### Post by techstop on 2009-10-18
Some very poorly written web sites check the browser, and fail to work if it's not IE. To get around this, try the User Agent Switcher addon for Firefox;

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

IE under WINE is pretty drastic.

---

### Post by AlexDudko on 2009-10-18
[http://www.tatanka.com.br/ies4linux/page/Main_Page]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

---

### Post by kvarley on 2009-10-18
If you must get IE then you could try "playonlinux" it's in the repos. It's a wine gui basically which downloads the applications for you.

> [CENTER]sudo apt-get install playonlinux[/CENTER]

---

### Post by Hopalong on 2009-10-19
To all, my thanks and -
314: the bank insists on IE.
techstop: it doesn't like Agent Switcher either.
AlexDudko: try the URL you gave and you'll see why I don't want to go there.
vitium: I'm not writing scripts to play games with the bank, thank you!
  Finally, can someone answer ny origiinal question please. Where are all the WINE experts?

---

### Post by bodyharvester on 2009-10-19
> **Hopalong said:**
> Where are all the WINE experts?

the WINE sub forum...
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

dont know if you will get your answer though, ive never heard of anyone using IE on linux, cant you do internet banking on the Vista? it really may be the easiest option if your bank is as uncooperative as you say

---

### Post by P4man on 2009-10-19
> **AlexDudko said:**
> [http://www.tatanka.com.br/ies4linux/page/Main_Page]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

+1

although the site is now flagged as an attack site by firefox and google. I guess his server got hacked again, but ies4linux should still work and should be safe I guess? Ive used it for years now :s

---

### Post by P4man on 2009-10-19
> **Hopalong said:**
> To all, my thanks and -
314: the bank insists on IE.

If they insist on insecurity, switch banks, seriously.

>   Finally, can someone answer ny origiinal question please. Where are all the WINE experts?

The best answer was already given (tatanga's ies4linux) even though his site being flagged as "attack site". Ill check the script tomorrow and see if its unaltered. Essentially it just downloads stuff from wine and microsoft, so I dont except to find anything malicious.

---

### Post by P4man on 2009-10-19
just downloaded ies4linux and checked the script. It seems identical to the one I downloaded months ago, and all downloads in the script go to trusted servers like soundforge, microsoft, macromedia...

So.. open a terminal and type:

```
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux
```

That will give you a working IE on ubuntu.

---

### Post by DougieFresh4U on 2009-11-10
> **Hopalong said:**
>  I select it, choose 'Browse C:/ drive', click 'programfolder', click 'internet explorer', click 'iexplorer.exe@. I get a blank panel headed 'Wine Internet Explorer'. How do I access the net from here? - or should I be doing something quite different?
 


> **Hopalong said:**
> 
  Finally, can someone answer my origiinal question please. Where are all the WINE experts?

I also would like to know if there is an answer to your question.
A couple years ago there used to be a link in the Ubuntu Christian that was excellent as it would put and installer in your Internet menu and once you ran it, there was an Internet Explorer launcher in the Internet menu. Can't seem to find it any more :-k

---

### Post by Hopalong on 2009-11-27
Thanks, but I've capitulated and use each bank separately, doing the adding up myself.  (I've got rid of Vista as an after-effect.);)

---

### Post by Hopalong on 2009-11-27
Thanks all, but I've capitulated, and log on to each bank separately (what it is to be rich!) That has enabled n=me to get rid of you know who.  ;)

---

### Post by Hopalong on 2009-11-27
Thanks all, but I've capitualated and now access each bank separately, doing my own adding up.

---

### Post by Hopalong on 2009-11-27
Thanks all, but I.ve capitulated, and access each bank separately. :rolleyes:

---

### Post by Norm24 on 2009-11-27
Just for grins I installed ie6 and ie7 through PlayOnLinux.I'm currently accessing this site with ie6.POL uses ie4linux to install ie6.

Ie7 was very quirky.Didn't work very well.

Not to hikack but POL makes using Wine easier that's for sure.I've always had issues with Wine in the past,but that never really bothered me as I don't use anything Win-based anyways.But POL is fun to play around with.

---

### Post by HuaiDan on 2009-11-27
POL simply automates the process. It still uses ies4linux to install ie6, ie7 appears to install a bit differently.


Folks, try it with the new kernel (2.6.31-15-generic).
I banged my head up against a wall for days trying to get ie6 to run on Karmic on a Dell 1420, and every time I visited a site that required flash, wine would crash.
Then came the new kernel update, and the inevitable video driver reinstall.

More wine-induced headbanging, and presto chango, wine+ies4linux+ie6 WORKED like a champ.

---

