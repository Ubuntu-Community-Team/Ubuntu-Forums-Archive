---
title: "ms-sys anyone used it?"
date: 2010-09-29
forum: General Help
---

### Post by slooksterpsv on 2010-09-29
Has anyone here used ms-sys to restore the bootloader/mbr on their machine to get back to Windows? If not, would someone want to try and see how hard it is to setup (booting only into a live-cd on a drive that has windows and ubuntu) and see if they can get it to work?

The reason I ask is cause a lot of people come and try Ubuntu, accidentally install it and want to get the regular windows bootloader back onto their system.

That way if someone has a problem, they can go through a how-to guide on the forums and see if it works.

---

### Post by drs305 on 2010-09-29
Yes, I've used it without problems. 

The app-du-jour (or perhaps app-du-yesterday since it's been around longer) on the forums though seems to be *lilo*. It works well - you run the following commands - will drop some messages about needing to be installed, but all you are using it for is to recover the MBR and not trying to completely install *lilo*

```

sudo apt-get install lilo
sudo lilo -M /dev/sd**X** mbr
```
Example: sudo lilo -M /dev/sda mbr

This thread is also very good at providing help restoring the Windows MBR:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

