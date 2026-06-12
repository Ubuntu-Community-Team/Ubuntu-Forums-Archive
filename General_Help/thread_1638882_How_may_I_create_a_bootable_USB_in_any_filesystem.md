---
title: "How may I create a bootable USB in any filesystem"
date: 2010-12-06
forum: General Help
---

### Post by sefs on 2010-12-06
That is...

1) DOS
2) FAT 16 (same as DOS?)
3) FAT 32
4) NTFS
5) ext*

Is there a generic way of doing this?

Thanks.

---

### Post by TheAnachron on 2010-12-06
Tbh, I don't think so. 
Windows realizes autorun.inf files, about ubuntu, I don't know. Mac is even more agressive about that kind of programs.

If you really want to make it universal, write a few lines in JAVA to start a few programs.

I think there is no better way.

---

### Post by dandnsmith on 2010-12-06
The stuff on the USB device has to be accessible to the code available to the BIOS on your motherboard, if it is to stand the remotest chance of being bootable. That usually reduces it to a simple FAT based system (number of bits being dependent on the size of the filesystem to be used and the device size).

You then need a system which can bootstrap in - for non-HDD you will, for linux systems, end up using SYSLINUX, ISOLINUX or another of that class (google for more info).

HTH

---

### Post by oldfred on 2010-12-06
I installed the Neo windows repair CD to a USB that  allows booting windows. Then I installed grub2 and it lets me still boot the windows repair or any ISOs I copy, chainboot, or boot any other partition. Usually I just add a generic partition boot and if necessary manually edit it to let me boot other partitions or chainboot to another drive.

Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
GRUB 2: A Guide for Users 
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

Rescue CD and boot grub2 floppy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)
Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)

---

### Post by C.S.Cameron on 2010-12-06
> **sefs said:**
> That is...

1) DOS
2) FAT 16 (same as DOS?)
3) FAT 32
4) NTFS
5) ext*

Is there a generic way of doing this?

Thanks.

Gparted will let you format in the above file systems and it will allow you to set the boot flag for that partition but that does not mean that any o/s or program put on that partition will necessarily be bootable.

---

### Post by sefs on 2010-12-07
What I am really trying to do is have a boot usb to boot with so that I can flash a bios.  But then I was curious as if there was a way to create a bootable usb for any os.  For instance the HP store tool can create a bootable dos usb.

GParted is a good start to get it formated and set it bootable I suppose.

---

### Post by dandnsmith on 2010-12-08
It's the BIOS limitations you have to be concerned with, not any OS (as the OS only gets loaded and into the picture further down the line).
It isn't sufficient just to mark something bootable, you have to get a workable load sequence, starting from the BIOS invocation.

What works on one PC may well not work on another, just for that reason.

Good luck in your quest

---

