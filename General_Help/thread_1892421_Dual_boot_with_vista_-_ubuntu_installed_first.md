---
title: "Dual boot with vista - ubuntu installed first"
date: 2011-12-07
forum: General Help
---

### Post by cjprofile on 2011-12-07
hi, i need help . i want to dual boot my ubuntu with vista.. and i dont know how to do it.. i tried to research and it looks so difficult to do.. help me... thanks

---

### Post by bluexrider on 2011-12-07
> **cjprofile said:**
> hi, i need help . i want to dual boot my ubuntu with vista.. and i dont know how to do it.. i tried to research and it looks so difficult to do.. help me... thanks

Please read this post [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

**Have a Windows recovery CD/DVD available**

---

### Post by oldfred on 2011-12-08
Since Windows will over write grub in the MBR, you also need an Ubuntu liveCD/USB of the current version you have installed. 

The NTFS partition you create must be a primary partition (sda1 thru sda4) and you need to use gparted to put a boot flag on it, so Windows sees it as the active partition. Otherwise the link bluexrider provided is pretty good.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

---

