---
title: "ubuntu 11.04 Ubuntu Classic how do I view what video card driver I am using?"
date: 2011-09-15
forum: General Help
---

### Post by s0nicfreak on 2011-09-15
Googled and it says to go to System > Administration > Hardware Drivers but there is no Hardware Drivers in there for me! I also tried going to Additional Drivers but there is nothing in there.

---

### Post by LowSky on 2011-09-15
Nothing there means you may only have access to an open source driver.
Only the proprietary drivers show up in that location. 
If you use Intel there isn't one, only AMD(ATI) and Nvidia use proprietary drivers.

If you still wanna know what video card you have open Terminal

type or copy/paste this command

```
lspci
```

look for VGA compatible controller.

---

### Post by s0nicfreak on 2011-09-15
Thank you. Is there no graphical way to view open source drivers?

---

### Post by 3rdalbum on 2011-09-15
> **s0nicfreak said:**
> Thank you. Is there no graphical way to view open source drivers?

You could locate, download and install a program and click the mouse button several times... or you could copy and paste a couple of letters into a terminal. The latter is easier to do and less likely to be done incorrectly :-)

Usually, if there's no video driver listed in Additional Drivers, then congratulations: You're already using the only driver that can be used.

The output of the 'lspci' command would just allow us to confirm that for you.

---

### Post by haqking on 2011-09-15
> **s0nicfreak said:**
> Thank you. Is there no graphical way to view open source drivers?


If you dont like the CLI then if you must you can install device manager from software centre which is a GUI very like the one in Windows.

but far simpler is ctrl+alt+t lspci ;-)

---

### Post by raja.genupula on 2011-09-15
```
sudo lshw -C display
```
its also going to provide the details your video drivers

---

### Post by Synoc on 2011-09-15
+1 for lspci. it really is simple and efficient. the only addition would be 

```
 lspci | grep VGA 
``` to filter our extraneous information.

---

