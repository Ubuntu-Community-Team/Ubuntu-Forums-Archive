---
title: "freezes+bug at startup"
date: 2010-04-23
forum: General Help
---

### Post by xarune on 2010-04-23
Hi,

I am trying to install Xubuntu on a old toshiba satellite A55. I threw in the live CD and did the try without any changes to your computer. The starts to load, when it finishes loading, and I can finally start poking around it freezes right away. When it freezes the graphics get a bit messed up, little ghost images next to their actual image appear (like a second icon of the same thing slightly offset, and blue/white) I had the same problem with Mint. Only thing I have been able to get running is puppy linux.

Any idea how to fix this?

Laptop info:
Celeron M CPU
roughly 750mb ram
ata-100 western digital drive
Toshiba Satellite A55-S3062

---

### Post by cariboo on 2010-04-23
Depending on what version you are using, < Lucid press F4 and select safe graphics mode. For Lucid press the any key at the initial screen, then press F6 and select nomodeset, then continue on to the desktop.

---

### Post by xarune on 2010-04-23
Ran it with safe graphics mode:

It did quite of bit of loading, then went to a blank screen with a small white underscore in the top left that is not blinking.... Also when this happened to CD in the drive stopped spinning.

---

### Post by nl4m on 2010-04-23
I had some problems with Ubuntu freezing on me too. Now the problems are gone. All I did was go to my desktop, right click, click on "Change desktop background", click on the "Visual Effects" tab and click on "None". It had to be this or an update that solved my problems. 

Or maybe you can boot into signal user mode/recovery mode and when you get to the command prompt type in "STARTX". It may solve the problem.

---

### Post by xarune on 2010-04-24
I tried the "startx" command and that did not work, it still froze.

As for right clicking the background, I can't do that because it freezes before I can do anything

---

