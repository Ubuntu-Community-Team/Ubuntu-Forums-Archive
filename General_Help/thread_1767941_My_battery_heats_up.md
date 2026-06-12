---
title: "My battery heats up"
date: 2011-05-26
forum: General Help
---

### Post by uShafee on 2011-05-26
My laptop lights started flashing on me. So i did a search for the flash code and it was a warning for battery heating up. This happens normally when i am on youtube (on AC power). It happens often.

Did this happen to anyone else? what should i do?

on Ubuntu 11.04 | Dell inspiron 14R

---

### Post by dargaud on 2011-05-26
the usual culprit is the flash player which uses a huge amount of CPU even when not actively playing any video. You can simply kill it, it will relaunch at the next video you open:
```
$ killall npviewer.bin
```
Although in 11.04 and/or FF4 it seems to have been folded into the plugin container... Don't know if you can kill that safely.

---

### Post by uShafee on 2011-05-31
yeah. it seems to be the flash player. However, since i installed 64bit ubuntu, i av not had this problem.

thanks.

---

### Post by uShafee on 2011-05-31
yeah. it seems to be the flash player. However, since i installed 64bit ubuntu, i av not had this problem.

thanks.

---

