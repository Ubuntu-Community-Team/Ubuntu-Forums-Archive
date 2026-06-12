---
title: "tvtime video artifacts"
date: 2006-04-24
forum: General Help
---

### Post by paulprovost on 2006-04-24
Hi all,
    I'm getting video artifacts in tvtime (see attached image) on image motion or change. xawtv display is fine. This is using an Asus tv/fm card (saa7133) and the saa7134 driver. everything is fine (tuning, audio), but I have these lines in tvtime. I am using an nVidia card with the "nv" drivers, if that matters.

Here's the "tvtime -v" output:

```
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/paul/.tvtime/tvtime.xml
cpuinfo: CPU Pentium III (Coppermine), family 6, model 8, stepping 6.
cpuinfo: CPU measured at 935.118MHz.
tvtime: Cannot set priority to -10: Permission denied.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 60900000
xfullscreen: Single-head detected, pixel aspect will be calculated.
xfullscreen: Pixel aspect ratio on the primary head is: 1/1 == 1.00.
xfullscreen: Using the XFree86-VidModeExtension to calculate fullscreen size.
xfullscreen: Fullscreen to 0,0 with size 800x600.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: EWMH check failed on child window, stale window manager property on root?
xcommon: Window manager is not EWMH compliant.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 66: NV Video Overlay.
speedycode: Using MMXEXT optimized functions.
station: Reading stationlist from /home/paul/.tvtime/stationlist.xml
videoinput: Using video4linux2 driver 'saa7134', card 'ASUS TV-FM 7133' (bus PCI:0000:01:00.0).
videoinput: Version is 526, capabilities 5010015.
videoinput: Width 720 too high, using 704 instead as suggested by the driver.
videoinput: Maximum input width: 704 pixels.
tvtime: Sampling input at 704 pixels per scanline.
mixer: Can't open device /dev/mixer, mixer volume and mute unavailable.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (60).
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 753x565 window inside 798x565 space.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 800x600 window inside 800x600 space.
field: 0 chan 0, ital 0, ul 0, colour 0xffffffff, indent 16, row 13
vbiscreen: Indent: 16, ital: 0, colour: 0xffffffff, row: 13
xcommon: Window fully obscured, marking window as hidden (116).
xcommon: Received an unmap, marking window as hidden (118).
xcommon: Received a map, marking window as visible (118).
field: 0 chan 0, ital 0, ul 0, colour 0xffff0000, indent 0, row 13
vbiscreen: Indent: 0, ital: 0, colour: 0xffff0000, row: 13
tvtime: Cleaning up.
Thank you for using tvtime.

```
Thanks for any advice!

---

