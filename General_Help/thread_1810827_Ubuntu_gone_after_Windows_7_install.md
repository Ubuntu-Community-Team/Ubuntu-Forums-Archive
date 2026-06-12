---
title: "Ubuntu gone after Windows 7 install"
date: 2011-07-23
forum: General Help
---

### Post by cjschris on 2011-07-23
Hi everyone.
I had a Windows 7 and Ubuntu 11.04 dual boot.
I recently re-installed Windows 7 and now when I start up my computer GRUB isn't there.

Does anyone have instructions on how to fix this?
There are heaps of turorials online, but I really don't want to use an outdated one, especially when it involves something as crucial as this.

Thanks and let me know if you need any info.

---

### Post by oldfred on 2011-07-23
You need to follow the instructions for reinstalling grub2 not grub legacy from the Ubuntu liveCD. Be sure to use the same version liveCD as your install. The simple short version should work and only if it does not work then you have to use the full chroot method.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

