---
title: "problem with ATI AH3450"
date: 2010-01-04
forum: General Help
---

### Post by mick1303 on 2010-01-04
Can somebody kindly point me to the thread discussing ATI AGP video card AH 3450.
I&#8217;m trying to make Ubuntu 9.10 to work with it. My hardware is:

MB GA-8PE667 with AGP 4.0, CPU P4 2.66. Chipset I845.

I&#8217;m trying to make dual boot with WinXP SP3 as a second OS. Windows part went fairly well. Managed to pass sound through HDMI and all that.

I&#8217;ve installed Ubuntu 9.10 and then without rebooting installed restricted drivers from ATI. I did it on the prompt from update manager. Internet worked via wireless card, which was immediately recognized by Ubuntu.

Then after first reboot I&#8217;m getting a black screen with mouse cursor.
If I hit CTR-ALT-F1 and go to command line, I can log in to the text mode. Here I&#8217;m at loss though. Looking through similar threads, I&#8217;ve managed to do &#8220;tail messages&#8221; in /var/log/

What it says is:
agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
pci 0000:01:00.0: putting AGP V2 device into 4x mode
[drm] Setting GART location based on new memory map
[drm] Can&#8217;t use AGP base @0xe0000000, won&#8217;t fit
[drm] Loading RV620 CP Microcode
[drm] Loading RV620 PFP Microcode
[drm] Resetting GPU
[drm] writeback test failed
hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
ratelimit.c: 13 events suppressed 
ratelimit.c: 4 events suppressed
[drm] resetting GPU

This was a second try to install Ubuntu. On the first try I just installed it and then went to reboot. It behaved the same - black screen with mouse cursor which I can move. I've assumed that it was for the lack of proper video drivers and on the second try installed them. Nothing changed - the log above is taken after the boot attempt on the 2nd try (with drivers presumably installed).

I&#8217;m fairly inexperienced with Linux. Had some experience with Solaris, but not as admin, but rather as a user. 

Not sure that my wireless is working in this mode though, so more likely the solution should be based on the premise that Internet is unavailable until I&#8217;ll manage to go to the graphics mode and Gnome. 

Any help is appreciated

Forgot:
If in the text mode I hit CTR-ALT-F7 - I'm getting to the graphics mode - it seems that it is a Gnome screen with upper and lower panels. But at this time the mouse is stuck and all I can do is to reboot.

---

### Post by mick1303 on 2010-01-05
I've managed to mount usb drive via command line and copied over the xorg.log file from /var/log/

Here it is:

---

### Post by mick1303 on 2010-01-11
I’ve read here (or somewhere else) that Koala works w/o Xorg.conf as a default, but if Xorg.conf is present – it has a priority. Maybe somebody has similar AGP ATI video adapter and older version of Ubuntu? Could you post your Xorg.conf as an example? I would try to run my system with it, or at least use a starting point.

---

