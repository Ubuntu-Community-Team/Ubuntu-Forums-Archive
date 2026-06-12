---
title: "Firefox Crashes"
date: 2012-03-19
forum: General Help
---

### Post by putnam120 on 2012-03-19
I'm running Ubuntu 11.04 on a Toshiba Portege. The problem is that Firefox will crash for no obvious reason on certain websites. I don't think it's a Flash problem (thought I could be wrong).
The problem has persisted even after updating FF and my kernel (which is now 3.0.0-0300-generic). I finally decided to run FF from a terminal to see what kind of error message I would get when it crashed and this is what was output.

> 
###!!! ABORT: X_CopyArea: BadMatch (invalid parameter attributes); 2 requests ago: file /build/buildd/firefox-12.0~b1+build2/build-tree/mozilla/toolkit/xre/nsX11ErrorHandler.cpp, line 190


Can anyone tell me what this means, or how to fix the problem?

---

### Post by mraandtux on 2012-03-19
Try reinstall Firefox?

---

### Post by Bucky Ball on 2012-03-19
Yea, I am having the same problem on three machines with the new Firefox update. Firefox randomly crashing on all of them for a month/month and a half. 

Sometimes boot the machine, boot Firefox and get the error 'How embarrassing! Firefox has dropped all your tabs,' or whatever. Other times, yea, I open a page, or it has happened when I've opened another app, and down she goes; 'Firefox has unexpectedly crashed.' And then it doesn't retrieve the tabs it's dropped when it asks 'would you like Firefox to attempt to retrieve tabs from last session?' (Not verbatim but you get my drift.)

Sucks. We have an 8.04 LTS machine, though (don't ask, long story), using an older Firefox and all sweet. I'm thinking of exploring the possibility of downgrading Firefox to the previous, stable, version.

* Incidentally, I also have a Toshiba (Sat Pro L510) but I don't think that is our issue here. Happening on my wife's Compaq and on my home brewed Frankenstein's desktop computer ...

---

### Post by putnam120 on 2012-03-19
> **mraandtux said:**
> Try reinstall Firefox?

Yeah I've tried reinstalling Firefox a few times, but it doesn't seem to have helped.

---

### Post by HiImTye on 2012-03-19
try using:
```
firefox --safe-mode
```
and disabling your add-ons

---

### Post by Subidubi32 on 2012-03-19
Have you tried to install older version of firefox, or one of the BETAs? Urora, Nightly etc..?

---

### Post by putnam120 on 2012-03-19
I have tried using safe-mode and the problem still persist. 
As for using older versions of FF how do you go about doing that?

---

### Post by Subidubi32 on 2012-03-20
[http://www.mozilla.org/en-US/firefox/all-older.html](http://www.mozilla.org/en-US/firefox/all-older.html)
Give it a try! I wish the best!
____________
Bence

---

### Post by Subidubi32 on 2012-03-20
[http://ubuntuforums.org/showthread.php?t=1916285&highlight=firefox](http://ubuntuforums.org/showthread.php?t=1916285&highlight=firefox)

This might be useful too.

---

### Post by putnam120 on 2012-03-20
Thanks, installing an older version of Firefox seems to have fixed the problem. Not sure why this worked though.

---

### Post by Bucky Ball on 2012-03-20
I got Firefox updates in the regular Update Manager last night and so far so good. I am using 11.0.

---

