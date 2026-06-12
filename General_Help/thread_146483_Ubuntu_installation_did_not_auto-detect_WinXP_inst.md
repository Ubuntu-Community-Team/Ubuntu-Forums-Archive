---
title: "Ubuntu installation did not auto-detect WinXP installation"
date: 2006-03-18
forum: General Help
---

### Post by goober99 on 2006-03-18
I have a 120GB (master/hda) and a 40GB (slave/hdd) hard drive. I have had Windows XP installed on the 120 and Ubuntu on the 40, but I decided to switch last night. I installed Windows XP onto hdd. Boots to Windows. Everything working fine.

Then I installed Ubuntu on hda. The Ubuntu installation did not auto-detect my Windows XP installation and add it to the GRUB boot loader. Now when I boot my computer, I only have the option to boot Ubuntu. The Windows installation is still there. I can mount it read-only within Ubuntu. What do I need to do to be able to boot to Windows XP again?

---

### Post by Zelut on 2006-03-18
It sounds like just a simple issue with the grub boot loader.  I'm assuming you have that installed?  (Does it mention grub during boot & a quick 3 second countdown?)

Can you output the results of "sudo fdisk -l"?
...with that information we can add the the appropriate listing to the grub menu & give you access to your windows partition at boot again.

---

### Post by goober99 on 2006-03-18
Yes, GRUB is installed, but my only choice is Ubuntu. Here is the output of "fdisk -l".

```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14405   115708131   83  Linux
/dev/hda2           14406       14593     1510110    5  Extended
/dev/hda5           14406       14593     1510078+  82  Linux swap / Solaris

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        4864    39070048+   7  HPFS/NTFS

```

---

### Post by aysiu on 2006-03-18
Sometimes Windows doesn't like not being on the first hard drive if Ubuntu's on the second, but Ubuntu didn't even *try* to add Windows to the Grub menu? That's odd.

---

### Post by goober99 on 2006-03-18
When I had Windows installed on the first hard drive, and I installed Ubuntu, Ubuntu did add Windows to the boot loader. Windows was booting fine from the second hard drive before I installed Ubuntu this time, and, no, Ubuntu did not even try to add Windows to the boot loader.

---

### Post by Lunixfanboy on 2006-03-18
I can't speak for the failure to detect Windows on /dev/hdd, but when you had Windows loaded on /dev/hdd a certain portion of it was still written to the Master Boot Record on /dev/hda. When you installed Ubuntu, grub overwrote that info, which might be why it didn't find it. To get Windows to boot using the grub bootloader, try the following: 
```
map (hd0, hd3)
map (hd3, hd0)
makeactive
chainloader +1
```
as the lines under the Windows section in grub. That will have grub pretend that hdd is hda and vice versa, and then make hdd the active partition and try to load the boot portions of Windows.

---

### Post by goober99 on 2006-03-18
Thanks for the suggestion. Unfortunately, no luck. I got the following error from GRUB:

```
map (hd0, hd3)
Error 11: Unrecognized device string
Press any key to continue...
```

But then I thought to myself, silly me: there is no reason the larger hard drive has to be set up as the primary hard drive. Since I want Linux on the larger hard drive, I am going to switch it to be the slave and make my 40GB hard drive the primary and just reinstall Windows on the 40GB.

---

