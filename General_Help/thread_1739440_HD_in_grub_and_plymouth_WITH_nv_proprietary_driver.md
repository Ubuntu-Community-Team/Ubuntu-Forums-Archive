---
title: "HD in grub and plymouth WITH nv proprietary driver?"
date: 2011-04-25
forum: General Help
---

### Post by gufide on 2011-04-25
Just want to know if I can put a resolution of 1366x768 in my grub and plymouth? I using NV driver, installed with jockey-gtk. No one know the solution here? Thanks you very much

---

### Post by Quackers on 2011-04-25
Yes you can.
You need to edit /etc/default/grub file for that.
In a terminal enter
```
gksu gedit /etc/default/grub
```
In the file which opens up create this line
```
GRUB_GFXPAYLOAD_LINUX=1366x768
```after this line ```
#GRUB_GFXMODE=640x480
```
Then save the file and then quit the file.
Then in the terminal run ```
sudo update-grub
```

Please note that this resolution must be supported by your screen. If it isn't, it may not boot!
Here is a guide on editing this file (amongst other things)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by gufide on 2011-04-26
crap... it didn't support my native resolution... I can get a 1024x768 (4:3) and not 1366x768 (16:9) but it still better... thank!

---

### Post by Quackers on 2011-04-26
Better than nothing though :-)
You're welcome.

---

