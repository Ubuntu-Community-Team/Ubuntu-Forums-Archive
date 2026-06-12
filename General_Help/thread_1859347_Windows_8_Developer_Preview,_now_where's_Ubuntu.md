---
title: "Windows 8 Developer Preview, now where's Ubuntu?"
date: 2011-10-13
forum: General Help
---

### Post by Teeba on 2011-10-13
Hi all :)
 
I recently installed the Windows 8 Developer Preview OS on a separate partition to that of my Windows 7 and Ubuntu installs.
 
Before I installed 8, when I booted up my computer I'd be presented with a list of bootable OSes (windows and Ubuntu with their respective safe modes). Now when I boot up my machine, I'm given the windows 8 dual boot selection screen instead, which is only between Win7 and Win8 of course.
 
How can I get rid of this new dual boot screen and revert back to my old one? Is there any way I could do this through the BIOS or something?
 
I want my Ubuntu back :(
 
Thanks,
 
Teeba

---

### Post by dcstar on 2011-10-14
> **Teeba said:**
> Hi all :)
 
I recently installed the Windows 8 Developer Preview OS on a separate partition to that of my Windows 7 and Ubuntu installs.
 
Before I installed 8, when I booted up my computer I'd be presented with a list of bootable OSes (windows and Ubuntu with their respective safe modes). Now when I boot up my machine, I'm given the windows 8 dual boot selection screen instead, which is only between Win7 and Win8 of course.
 
How can I get rid of this new dual boot screen and revert back to my old one? Is there any way I could do this through the BIOS or something?
 
I want my Ubuntu back :(
 
Thanks,
 
Teeba

AFAIK Windows 8 uses a totally different BIOS boot method that **NO OTHER OS** is currently compatible with (and it will **only** boot other Windows OSs).

Uninstall Windows 8 if you want Ubuntu back.

---

### Post by oldfred on 2011-10-15
I think dcstar's comment are about the new UEFI mode. But several have installed Windows 8 in BIOS mode and it is just like Windows 7 so far. Does Windows 8 also create a separate /boot & recover partition or share the Windows 7 one?

All windows (and most systems) install their boot loaders when you install the system. You need to reinstall grub2's boot loader.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)


Did you install Windows 8 in a primary partition? The second install of Windows moves all the boot files to the partition with the boot flag or active partition.

Multibooters, Pictures here worth 1000+ words, mostly Vista, but 7 is same except it has another 100MB boot/recovery. 
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly (older now)
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

