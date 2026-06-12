---
title: "32&quot; LCD as Monitor, Resolution Problem"
date: 2010-11-12
forum: General Help
---

### Post by sjl127 on 2010-11-12
Thank you, 

I have a LG 32" LCD TV as a monitor, however, having a resolution problem, specifically, the horizontal placement of the screen, it's a little off to the right...

How do I move this back over to the left?  No auto adjust on TV...

---

### Post by Eskobar on 2010-11-12
Did you install Ubuntu while it was connected to the 32 inch?

 I had problems when I first connected my machine (Lucid) to my tv (older model 32 inch LG)...at first it wouldn't display at all, until I rebooted.   After I rebooted, the picture was distorted.   I reinstalled, quickly pressing F6 while the purple install screen is loading (when the keyboard + monitor symbol are at the bottom of the screen) and selected "nomodeset", it installed fine...but if your computer requires additional graphic drivers, you will run into problems later on.   There may be a simpler way to fix this...but I'm no expert, so I'm just sharing what is currently working for me.   

I reinstalled on my regular 19 inch monitor...drivers & system fully updated...then i power off my machine.......connect it to my tv......power up my machine....and of course, make sure you have selected the right input (vga, video 1, video 2, etc).  Hope this helps.

(SN:  If you can get to  SYSTEM >> PREFERENCES >> MONITORS...the display setting on my TV is 1280 x 768   That adjusts the monitor...there is a button that says "detect monitor".

---

### Post by efflandt on 2010-11-12
How are you connected to the TV, VGA or digital (HDMI or DVI to HDMI)?

And what video card/chip do you have and are you using default video modules or proprietary ATI or NVIDIA drivers?

I have NVIDIA GT 220 using nvidia drivers connected DVI to HDMI before and now using HDMI.  I was surprised that if I set my LG 32LH40 1080p HDTV to 16:9 it ends up overscanned all around, cutting off part of top/bottom panels.  But fortunately the TV has a "just scan" mode that matches it to the video signal and is perfect for 1920x1080, or switched to 1360x768 or 1280x720.

It worked fine with my older PC too using DVI to HDMI with an older ATI card and default video drivers.

However, its "just scan" does not work for VGA or if you tell it other input is a PC.  Modelines returned by **cvt** or **gtf** for **1920 1080 60** resulted in a horizontally scrunched display when using **xrandr** commands on my laptop.  So I used a modeline for xrandr in a script from /var/log/Xorg.0.log that my old PC had determined automatically.  I thought that worked fine, but when I tried that lately it was shifted to the left.  So it would be nice to know which number(s) in a modeline need to be adjusted to simply shift the image left or right.  For some reason I can never get **xvidtune** to allow me to "apply" any changes to see if they help.

---

