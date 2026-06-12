---
title: "100% CPU load when selecting"
date: 2006-02-18
forum: General Help
---

### Post by thepocketdrummer on 2006-02-18
Whenever I go to select mulitiple files, the blue square kind of lags up and my CPU load goes all the way up to 100% If I move it around long enough, other programs slow down or stop (in the case of music).

What is the problem and how do I fix it?

---

### Post by coolclassic on 2006-02-18
Have a look at top to find out whats using your cpu.

---

### Post by DarkT on 2006-02-18
Have you got a graphics card drivers installed? I think this is happening because the CPU is trying to do the job of the GPU with the transparency of the selection box (I could be wrong on that specific though) as I've found installing graphics drivers (with appropriate xorg.conf edits) and turing on Option RenderAccel for your card in xorg.conf resolves this and other graphical slowdowns.
 
I don't know how to do it for ATI cards(if you search you'll probably find out how:)) but for NVIDIA there are debs or you can use the NVIDIA installer if you want a newer version of the drivers... I think there is a thread n the "Customization Tips And Tricks Forum" which can guide you through setting up your graphics card. Hope that helps :)

---

### Post by Denta on 2006-02-19
Yes, if on Nvidia try adding 
**Option		"RenderAccel"  "True"**
to your /etc/X11/xorg.conf in section Device

---

### Post by thepocketdrummer on 2006-02-20
The renderaccel one worked, Thanks!

---

