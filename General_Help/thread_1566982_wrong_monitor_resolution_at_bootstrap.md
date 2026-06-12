---
title: "wrong monitor resolution at bootstrap"
date: 2010-09-03
forum: General Help
---

### Post by Gingalone on 2010-09-03
Sometimes, randomly, when turning on my Ubuntu laptop (HP 6730b, Ubuntu 10.04) I get a wrong monitor setting (much lower resolution than normal) and it is not possible to set it correctly because the menu buttons are wrongly placed and some are not present (probably there is not enough room for them) I have no other way than to restart the system to get the right resolution.

Can someone tell me  this inexplicable (to me) behaviour? 
Of course I didn't change anything in monitor settings...

Thanks for any help.

---

### Post by djcasey on 2011-02-01
I have the same problem on my laptop, also an HP 6730B.

---

### Post by Krytarik on 2011-02-01
Follow this guide to set the resolution, either by using xrandr at startup or by xorg.conf:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Brandex07 on 2011-05-08
I had a similar issue with my toshiba l505 laptop and it  was driving me crazy. I finally figured out if you go into monitor  preferences, within ubuntu, the menu will show that there are two  displays in detection. If you click on the "unknown" monitor and click  "off" and fix "laptop" resolution to its highest, save as default and  reboot, the issue seems to go away.

---

