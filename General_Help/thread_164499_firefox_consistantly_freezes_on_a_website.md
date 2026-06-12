---
title: "firefox consistantly freezes on a website"
date: 2006-04-22
forum: General Help
---

### Post by cwmccabe on 2006-04-22
My wife likes to visit [http://www.huaren.us/](http://www.huaren.us/) but pages within the website consistantly cause Firefox to crash on my system.  I'm running Ubuntu 5.10 and Firefox 1.0.8.  Just now she tried the following link and I can confirm that every time we try to load it, the browser freezes: [http://www.huaren.us/dispbbs.asp?boardID=347&ID=196698&page=1](http://www.huaren.us/dispbbs.asp?boardID=347&ID=196698&page=1)  After it freezes and we have to force-quit the browser, the processor stays at 100%, with about 70% user and 30% system.  I then have to open the System Monitory and kill the firefox-bin process because it keeps running.

Can anyone suggest what could be going wrong here?  My wife is accumulating examples for why linux doesn't work very well and I'd like to demonstrate otherwise.

---

### Post by dermotti on 2006-04-22
Just for testing purposes, install epiphany and see if you get the same results. It uses the gecko engine installed with firefox.

---

### Post by codypumper on 2006-04-22
I had the same problem when I first installed Ubuntu. I have found a fix to it. First install Automatix:

To install Automatix in Ubuntu do the following from terminal(one line at a time, pressing enter after each step):
Code:

wget [http://beerorkid.com/automatix/automatix_5.8-1_i386.deb](http://beerorkid.com/automatix/automatix_5.8-1_i386.deb)
 sudo dpkg -i automatix_5.8-1_i386.deb

Then close all your windows and open automatix (Applications-->system tools) Click OK twice. Enter your password. Select Firefox 1.5.0.1 from then list then click ok and let it finish.

It should have fixed it.

---

### Post by z_diver on 2006-04-22
[QUOTE=cwmccabe]My wife likes to visit [http://www.huaren.us/](http://www.huaren.us/) but pages within the website consistantly cause Firefox to crash on my system.  

 I can confirm that every time we try to load it, the browser freezes: [http://www.huaren.us/dispbbs.asp?boardID=347&ID=196698&page=1](http://www.huaren.us/dispbbs.asp?boardID=347&ID=196698&page=1)  [/QUOTE]
I run the automatix version of firefox and I'm able to view both of the sites your wife has problems with at normal speed.

---

### Post by cwmccabe on 2006-04-22
Wow, i don't think this turned out the way it should have.  First I installed epiphany and confirmed that the website caused it to freeze.  Then I uninstalled firefox through synaptic and re-installed it using Automatix.  But, the Automatix-installed version would not start.  When I run 'firefox' from the commandline, I now get the following message:

```
/opt/firefox/run-mozilla.sh: line 131: 11159 Segmentation fault      "$prog" ${1+"$@"}
```

I then tried to uninstall firefox and reinstall it using synaptic, but I can't get it to work again.  (I'm posting this with epiphany right now.)

Any ideas?!  ](*,)   Thanks for all the suggestions so far.  I hope someone can help me out of this one!  Even if I don't get firefox to work with that website, I would at least like to get firefox to work again...

---

### Post by cwmccabe on 2006-04-23
Back to square one: I used list item #32 from here [http://ubuntuforums.org/showthread.php?t=90797](http://ubuntuforums.org/showthread.php?t=90797) to get back to the firefox I was using before.  Still no luck on the freezing website though...  any suggestions?

**EDIT:** I solved my problem, but it took a lot more work than I had expected.  I installed Firefox 1.5.0.2 after compiling it from source.  Problems solved.  I followed instructions on these pages:  (1) [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) and (2) [https://wiki.ubuntu.com/CompileFirefoxNewVersion](https://wiki.ubuntu.com/CompileFirefoxNewVersion)

---

