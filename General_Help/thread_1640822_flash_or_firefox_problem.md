---
title: "flash or firefox problem"
date: 2010-12-08
forum: General Help
---

### Post by karogi on 2010-12-08
Hi guys, I got a strange problem with firefox (or maybe with flash).
Let's say I run any video on youtube. After some moments video is stopped and video is colored grey color.

Look to the screen

---

### Post by TeoBigusGeekus on 2010-12-08
It seems that the flash plugin is crashing.
Try with another browser.

---

### Post by Lordluen on 2010-12-08
Do you have 64-bit ubuntu 10.10? If you do, flash 9 has issues with that. I reccommend downloading the newest pre-release of flash 10 for 64-bit linux systems. It did the trick for me! This is all of course, only if you have 64-bit ubuntu.

---

### Post by karogi on 2010-12-08
Yes, I got ubuntu 10.10 64bit.

---

### Post by philinux on 2010-12-08
> **karogi said:**
> Yes, I got ubuntu 10.10 64bit.

Have you enabled your video card drivers?

System>admin>Additional drivers

---

### Post by karogi on 2010-12-08
Yes. Everything work good, except this thing.

I don't see link to download flash 10 for 64bit system...

---

### Post by philinux on 2010-12-08
> **karogi said:**
> Yes. Everything work good, except this thing.

I don't see link to download flash 10 for 64bit system...

Try this.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by gandaran on 2010-12-08
> **karogi said:**
> Yes, I got ubuntu 10.10 64bit.
then you should remove every flash plugin installed and get the 64-bit flash [here]("http://labs.adobe.com/downloads/flashplayer10_square.html")
extract the package and put the libflashplayer.so file in /home/'user'/.mozilla/plugins or /usr/lib/firefox/plugins.

---

### Post by sydbat on 2010-12-08
> **philinux said:**
> Try this.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)+ Infinity. Flash-Aid is brilliant. Does it all for you. Removes conflicting apps and installs the correct Flash for your system.

---

### Post by karogi on 2010-12-08
Thanks guys, i think it fixed my problem.

---

