---
title: "Video plays but no video in Lucid Lynx"
date: 2010-04-24
forum: General Help
---

### Post by pillar007 on 2010-04-24
I just installed Lucid Lynx RC 1 on my MSI Wind U100 netbook.

When I tried to play a video on it I was informed of a lack of codecs, so I downloaded my video player of choice: VLC media player.

When I tried to play the video, there was audio but the screen was black.  The same thing happened when I downloaded to codecs and used the stock video application.

Thanks for your help!

---

### Post by melsu on 2010-05-05
Same problem here

Using Nvidia driver 173.14.22
tried also with nvidia-current drivers, but still no result
Also added medibuntu repositories and installed codecs. Sound is present, but no video is playing and no visualisation in rhytmbox as well.
Any ideas?

---

### Post by melsu on 2010-05-05
After doing some digging throug internet found the following solution:
Alt+F2 and then type gstreamer-properties
there change your video output to from automatic to X Window System (No Xv)
use test button to check.
:p

---

### Post by jmcdaid on 2010-05-28
Thanks! That worked for me on an HP Mini210 with Lucid Lynx. I was seeing no video on extended desktop unless in mirror mode, and the switch to no Xv did the trick.

---

