---
title: "four monitor trouble"
date: 2010-08-17
forum: General Help
---

### Post by olof_ on 2010-08-17
hello!
2 LCDs (19" and 23"), 2 CRTs (19",19").
using 1280 x 1024 resolution on the 19" monitors and 
1920 x 1080 on the 23" monitor.
to this i have 2 8800GTs.
using "nvidia-current", with Xinerama enabled.
two of the monitors are using "TwinView" and the two others are configured as "Separate X screen".
Ubuntu 10.04 x64
using ext4 with ~3GB swap

more PC spec: 3,6Ghz C2D intel, 8GB ram, a additional GPU: an ati 4850 which i figured out couldnt work toghether.

here comes the problem:
one of the monitors (CRT) configured as a "Separate X screen" a (HP M700 if it matters), is showing the wallpaper, can have windows open, is working just fine, *until* I move the mouse pointer there. When I do, the pointer will freeze there, causing the whole system to crash.

the other three monitors are working perfectly, without any strange behaviours at all.

here are a screenshot of my settings: [link]("http://pici.se/629746/")
the monitor which causes the problem is in the upper left part of the screen.

if someone even may have any clue, please just ask, I really want to switch to linux:)

---

### Post by yojimbo-San on 2010-10-14
Sounds like you may be bitten by [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539) ... have a look and subscribe/contribute to this report if appropriate.

---

### Post by yojimbo-San on 2010-10-14
Although that's odd, perhaps I didn't read carefully enough ... that bug is a 10.10 issue, not a 10.04 one. Not sure.

---

### Post by olof_ on 2010-10-16
Someone replied to my thread!
actually I solved the issue by re-installing everyting but now with Ubuntu 10.10, and this time I did'nt use Xinerama, but instead each screen as a separate X-server. 

Pros are that now Compiz is working, but the cons are I cant drag applications from screen to screen.

Thank you for trying to help, it is really true about ubuntu and its support.
Now I've been enyoying the good side for exactly two months:)

Do you know any alternatives to Xinerama (not Twin view) that enables me to drag windows from screen to screen?

edit:
thank you for the thread.

---

