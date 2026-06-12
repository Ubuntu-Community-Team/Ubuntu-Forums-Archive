---
title: "Font smoothing in browsers"
date: 2010-05-03
forum: General Help
---

### Post by yyx on 2010-05-03
After Installing 10.04, I've noticed that web browsers seem to be ignoring the font rendering settings set for the ui (System>Preferences>Appearance>Fonts).

So far I've tried Firefox, Chromium and Opera, and text renders equally blurry in all of them.  Changing from one rendering method to another has an effect on menu bars etc, but  doesn't change how text appears inside of a browser, for better or worse.

Can this be fixed, or is it just not supported?

---

### Post by lovinglinux on 2010-05-03
Try [this](http://lovinglinux.megabyet.net/?page_id=220#Firefox-display-weird-fonts,-with-greenish-blue-shadows,-after-update--2).

---

### Post by WilliamCampbellJr on 2010-05-03
I had the same issue. Apparently I had somehow had the NVIDIA accelerated graphics driver version 173 activated (which I don't think was part of my earlier Ubuntu version). Anyway, I downloaded the "current" version of the driver, which was recommended,  and removed the 173 version. Rebooted. The fonts all returned to normal.

---

