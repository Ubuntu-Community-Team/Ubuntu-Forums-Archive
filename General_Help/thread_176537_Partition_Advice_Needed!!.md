---
title: "Partition Advice Needed!!"
date: 2006-05-14
forum: General Help
---

### Post by kudu on 2006-05-14
Hi,

I have two hard drives installed.

hda (master) - MBR and Windows XP
hdb (slave) - ubuntu breezy

I use grub to boot, ubuntu is default O/S.

My question is how do I re-partition hda without messing up the MBR and my excellent ubuntu setup, which if memory serves installed grub to hda (MBR?). What I want to do is install gentoo on hda instead of Windows XP. I want a pure Linux machine. Help really really appreciated!

Thanks,
kudu

Here's what hda looks like:

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           4       32098+  de  Dell Utility
/dev/hda2   *           5        5904    47391750    7  HPFS/NTFS
/dev/hda4            5906        9729    30716280    f  W95 Ext'd (LBA)
/dev/hda5            5906        9729    30716248+   b  W95 FAT32


and here's what hdb looks like:

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9538    76613953+  83  Linux
/dev/hdb2            9539        9726     1510110    f  W95 Ext'd (LBA)
/dev/hdb5            9539        9726     1510078+  82  Linux swap / Solaris

Simple as can be!

kudu...out

---

### Post by bluevoodoo1 on 2006-05-14
Partitioning has always been the bane of my existence, but some advice:

Backup all important data before messing with your partitions!!!

---

### Post by towsonu2003 on 2006-05-15
I'm not sure if gentoo gives the option to do so (ubuntu livecd installer doesn't!), but if it does, tell it to install grub to **boot** instead of **mbr**. than boot ubuntu as you always do, and add the following to it at the end of the file: 

```

title            Gentoo
root            (hd0,x)
savedefault
chainloader     +1

```
x is a number that will change according to where you install gentoo. generally speaking, x = y - 1 (y is a number too) where /dev/hda**y** is the partition to which gentoo's boot directory (usually whichever partition gentoo is installed, unless you specified otherwise). 

example: 
In my mbr, 
```

title           Other Distro 2
root            (hd0,9)
savedefault
chainloader     +1

```
Title is anything you want. Other distro is installed (along with its /boot directory) to /dev/hda10. Basically, this line tells grub to go to /dev/hda10, find the boot loader there, and launch it. than the other distro's bootloader will take over and boot whatever it has in its list.  In my case, grub goes to /dev/hda10 (hd(0,9)) and launches Zenwalk's lilo bootloader installed to boot. Than lilo boots Zenwalk. 

Things you'll wanna do as well:
[list]
[*] have /home in a separate partition
[*] not delete /dev/hda1 which has Dell Utilities. 
[*] back up your data in case something doesn't work
[*] have a liveCD available if something goes wrong
[/list]

---

