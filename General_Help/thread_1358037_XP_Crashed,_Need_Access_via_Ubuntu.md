---
title: "XP Crashed, Need Access via Ubuntu"
date: 2009-12-17
forum: General Help
---

### Post by CottonTheMoth on 2009-12-17
Hi, I got a trojan on my XP partition apparently, and now Windows won't boot up, it just restarts once XP begins to load and then I'm back to booting XP, and so on. Unfortunately my unused space is 8MB, so I can't install the Ubuntu Live CD that I have onto a separate partition, or even update it from 8.10. At this point I'm just trying to gain access to my Windows files, and I'm having problems mounting the C: drive so that I can pull off files onto an external hard drive. Any help would be appreciated, I have photography that needs to be recovered :(! Thanks!

Oh, and GParted will not resize my XP partition even though it's like 320 GB.

---

### Post by n0glu3 on 2009-12-17
Do you have access to another PC with a disc burner and a spare CD?

---

### Post by CottonTheMoth on 2009-12-17
I could use a friend's if need be. I have Flash drives I could convert to boot an OS if that's what you think I'm needing to do. What do you suggest?

Oh, I'm on an EEEPC Netbook with XP by the way.

---

### Post by TetonsGulf on 2009-12-17
If you have an external DVD drive, pop in a LiveCd and you're all set to browse and copy the files.

Barring that, you need to have a bootable USB to do the same. UNetbootin will work on linux, windows and osx to convert an iso so thats probably your best bet. If you have a LiveCD already you don't even need to download and burn a new iso.

Check out UNetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Best of luck!

---

### Post by efflandt on 2009-12-17
If you can boot install CD on a system that has an install iso somewhere on one of its drives, you could use System > Administration > USB Startup Disk Creator to make a bootable live/install system on USB stick (or other memory like SD in USB card reader).  That works best if it is at least 2 GB.  It just uses regular fat or vfat partition.  If you make a persistent file, do not make it any larger than one click down from maximum.

If you want to install a regular system on USB (flash or hard drive), you need at least 4 GB, although, 8 GB minimum is recommended.  The USB partition would need to be formatted to a suitable filesystem (ext3, etc.).  You could do all that right from install CD.  But pay attention during the summary just before it proceeds with actual installation, to use **Advanced** button to put grub on the USB mbr (instead of default to main hard drive mbr).

When you want to boot the USB device, you need to watch your computer splash screen for the button to press to select the boot device, or setup key to get CMOS setup to change boot order.  In once case even when I selected USB as the boot device, it still booted from hard drive until I changed drive order in CMOS setup to USB before hard drive.

---

