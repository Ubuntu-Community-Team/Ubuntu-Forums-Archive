---
title: "NVIDIA Quadro NVS 450 ==&gt; Blank screen"
date: 2010-10-05
forum: General Help
---

### Post by jaezcurra on 2010-10-05
Hi, I have just bought a Dell Optiplex 960 with a NVIDIA Quadro NVS 450. Everything works out of the box with the 10.04.1 Live CD. It suggests to install and activate NVIDIA proprietary drivers, but you need to restart the machine afterwards.

The problem is that, after that, all what you get is a blank screen, with not even a cursor.

The same happens when you install Lucid: blank screen with no cursor.

Ctrl+F1 does not show anything, but Ctrl+Alt+Prnt Scrn+REISUB works and the PC is reset.

In the var directory the logs show that the NVIDIA module is not loaded.

Any suggestion to fix things in the hard disk from the Live CD?

---

### Post by searchfgold6789 on 2010-10-05
To make the Live CD pretend that it's root is actually your hard disk,
```
sudo mount /dev/sdXX /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
```
You can uninstall the nVidia drivers using that if you need to.

---

### Post by jaezcurra on 2010-10-05
See [http://ubuntuforums.org/showthread.php?t=1588648](http://ubuntuforums.org/showthread.php?t=1588648)

---

