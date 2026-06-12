---
title: "Some xrandr problems"
date: 2012-01-29
forum: General Help
---

### Post by Shinon Yoshida on 2012-01-29
Hi, I bought a TV that had a VGA plugin but I have found it to be difficult to use because it's supported resolutions are not automatically detected (it supports up to 1366x768). I found out it's because it (the TV) has no Plug n Play support. So I decided to use cvt to get my modelines manually and use xrandr to add it and it works. I use these two commands for it: ```
xrandr --newmode "1368x768"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1368x768
``` It works fine but after about 20-45 minutes (it varies) things get really messed up visually.

[[IMG]http://img825.imageshack.us/img825/9952/screenshotat20120125031.th.png[/IMG]]("http://imageshack.us/photo/my-images/825/screenshotat20120125031.png/")

[[IMG]http://img46.imageshack.us/img46/1891/screenshotat20120124140.th.png[/IMG]]("http://imageshack.us/photo/my-images/46/screenshotat20120124140.png/")

This makes it absolutely difficult to do anything after this happens. I have some speculation that it happens when I'm doing something resource intensive. 

If it helps, I'm using Ubuntu 11.10 i386 Desktop. I have tested the TV on Windows 7 on two different computers both with Windows 7 (one 32 bit and the other 64 bit) and Ubuntu 11.10. Both systems cannot detect correct resolutions.
These are also some of my hardware specs 
Graphics: Integrated Intel Graphics Media Accelator 950
CPU Intel Pentium 4 3.20 GHz
1 GB of RAM
It's a Dell OptiPlex GX620

I'm hoping for some workaround , I'd really appreciate some help. 
Thanks ahead of time :D

---

### Post by Shinon Yoshida on 2012-02-04
Bump

---

### Post by Shinon Yoshida on 2012-02-10
BUMP again... seriously no one can help?

---

### Post by sudodus on 2012-02-10
You have described your Ubuntu version. Please describe also your computer hardware:

- cpu, graphics chip, ram

If you have nvidia or ati radeon graphics, you may need a proprietary driver to improve the performance. What driver are you using now? Please post the output of the command 
```
glxinfo | grep OPENGL
```

If you don't know your hardware, please look at it with
```
gksudo lshw | less
``` and look for the sections

*-cpu
*-display
*-memory

---

### Post by Shinon Yoshida on 2012-02-13
Graphics: Integrated Intel Graphics Media Accelator 950
CPU Intel Pentium 4 3.20 GHz
1 GB of RAM

---

### Post by sudodus on 2012-02-13
> **Shinon Yoshida said:**
> Graphics: Integrated Intel Graphics Media Accelator 950
CPU Intel Pentium 4 3.20 GHz
1 GB of RAM
I think the computer side should be able to manage the resolution at a reasonable refresh rate of the TV. It is strange that the picture gets bad after some time. Can you see some small defects earlier (maybe after only a few minutes, long before 20 minutes)?
I'm thinking that maybe you are writing outside of some memory limits, so that the defects add up gradually. Maybe the TV set is made to show 1280x720 frame size: '720i' or '720p', so if you try that with cvt and if necessary setting a lower frame rate with the third parameter?

On my computer ```
cvt 1280 720
``` outputs
```
# 1280x720 59.86 Hz (CVT 0.92M9) hsync: 44.77 kHz; pclk: 74.50 MHz
Modeline "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
```
Would something like that work better?

Or have you tried really low resolutions, for example 800x600, if it works 'forever' without defects.

---

### Post by Shinon Yoshida on 2012-02-13
well cvt is where I got my modeline. The TV is 720p. I haven't tried custom low resolutions with xrandr but I'll try it out.

---

### Post by efflandt on 2012-02-13
You may have better luck using a 1360x768 mode instead of 1368x768, since there does not seem to be any mode exactly 1366x768.  Better to underdrive it a little than overdrive it and have it glitch.

I have used 1360x768 before on a 1080p HDTV, for a laptop that was limited to 1360x1360 max due to limited shared video RAM.

---

### Post by Shinon Yoshida on 2012-02-14
Well after testing a bit, I think it is a memory problem, whether it's video memory or RAM, I'll be upgrading my RAM and then my video card.
I did try it at 800x600, it still messed up after using up a bunch of RAM.

---

