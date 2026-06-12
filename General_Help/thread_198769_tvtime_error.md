---
title: "tvtime error"
date: 2006-06-17
forum: General Help
---

### Post by markthetech on 2006-06-17
I am new to Ubuntu and have figured out alot so far but this has me stumped.
I am trying to figure out why Tvtime when clicked on opens then shuts a split second later. I am useing a V-Stream terminator tv card that I know worked under windows XP. I opened a terminal window and typed tvtime -v and i got this. Can anyone explane this to me please.

mark@mark:~$ tvtime -v
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/mark/.tvtime/tvtime.xml
cpuinfo: CPU Intel(R) Celeron(R) CPU 2.50GHz, family 15, model 2, stepping 9.
cpuinfo: CPU measured at 2500.644MHz.
tvtime: Cannot set priority to -10: Permission denied.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 60802000
xfullscreen: Single-head detected, pixel aspect will be calculated.
xfullscreen: Pixel aspect ratio on the primary head is: 1368/1355 == 1.01.
xfullscreen: Using the XFree86-VidModeExtension to calculate fullscreen size.
xfullscreen: Fullscreen to 0,0 with size 1280x1024.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is Metacity and is EWMH compliant.
xcommon: You are using metacity.  Disabling aspect ratio hints
xcommon: since most deployed versions of metacity are still broken.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

---

