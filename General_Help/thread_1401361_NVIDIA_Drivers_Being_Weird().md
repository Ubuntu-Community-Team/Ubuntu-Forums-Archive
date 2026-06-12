---
title: "NVIDIA Drivers Being Weird(?)"
date: 2010-02-08
forum: General Help
---

### Post by KhRiZiZi on 2010-02-08
I just reformatted like 5times+ trying to fix this issue, happens with Lucid Alpha 2 & Karmic install. Once I install the driver my mouse stops working and same with my keyboard. As in the mouse laser just turns off and all lights on keyboard too, just kills them off.

---

### Post by KhRiZiZi on 2010-02-09
1 day old bump.

---

### Post by patchwork on 2010-02-09
What hardware is involved (Brands and specs if possible).  Also, can you post your Xorg.0.log?   It is found in /var/log


A little background, if your computer relies on the /etc/X11/xorg.conf (not all do anymore) to define the input devices, and your driver install is rewriting the file, it is possible that your input settings have been erased.

---

### Post by KhRiZiZi on 2010-02-10
> **patchwork said:**
> What hardware is involved (Brands and specs if possible).  Also, can you post your Xorg.0.log?   It is found in /var/log


A little background, if your computer relies on the /etc/X11/xorg.conf (not all do anymore) to define the input devices, and your driver install is rewriting the file, it is possible that your input settings have been erased.
Just wondering how I will do that without my mouse & keyboard working..

---

### Post by patchwork on 2010-02-10
Boot with a live cd.  You should be able to view (and edit) your xorg.conf.

---

### Post by Nunu on 2010-02-10
Is your mouse USB? i had a similar issue a while ago managed to get the mouse working by unplugging and plugging it back in.

---

