---
title: "Desktop Works slower after disabling Visual effects"
date: 2012-03-01
forum: General Help
---

### Post by yurmetal on 2012-03-01
Hey guys!!! I'm running Ubuntu 10.04 LTS on an old hardware. Everything is working perfectly but when i'm disabling visual effects, my desktop works slower. I mean when i want to see my desktop the desktop icons pop up slower and when im making a drag box with mouse it begins to freeze! Turning visual effects to normal solves this problem, but i don't want these effects to be on. Can anybody help me please, thanks!

---

### Post by raja.genupula on 2012-03-01
Hi Disabling Visual effects means ,If they are at normal means what basic Visual effects needed by the desktop for Proper look . so if you disable them means you are not enabling the required things to make the desktop for proper look  . like this what i am thinking . 

If you wanna improve system performance and you have less configuration then you better to switch to Lubuntu or Xubuntu . they are light weighted Ubuntu Versions suitable for less configuration systems . 

may i know what is your system configuration please . 

thank you .

---

### Post by yurmetal on 2012-03-01
Intel(R) Pentium(R) 4 CPU 2.66GHz
Memory 512 + 512
GPU GeForce2 MX/MX 400
HDD Seagate 80 GB

---

### Post by Krytarik on 2012-03-01
When you disable Visual Effects in any pre-11.04 version of Ubuntu, it disables Compiz as the window manager, and enables Metacity instead; for that, definitely make sure that compositing is enabled, everything should run much more fluent/stable then!:
```
gconftool-2 --set --type bool /apps/metacity/general/compositing_manager true
```Other than that, you can gear down Compiz' effects, you know. ;-) Therefore, use "CompizConfig Settings Manager". Personally, I prefer Compiz much over Metacity, not because of effects, but because of the many other features it offers - the actual *window managing* stuff. :D

Regards.

---

### Post by yurmetal on 2012-03-01
thank you for your help guys :)) with CompizConfig Settings Manager, I used to disable some effects.

---

