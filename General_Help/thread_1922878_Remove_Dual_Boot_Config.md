---
title: "Remove Dual Boot Config?"
date: 2012-02-09
forum: General Help
---

### Post by hbnmgr on 2012-02-09
Was running good up until recent updates. Now will not even boot.

Installed to Dual boot WinXP / Ubuntu, on two different drives, but want to eliminate the drive with WinXP and go with Ubuntu on a SATA drive only. So my question is how do I fix it to boot to the SATA / Ubuntu and therefore remove the dual boot configuration?

Thanks!
hbnmgr

---

### Post by cogier on 2012-02-09
Do you know which drive has "grub" on it?  If it is on the Ubuntu drive I suggest you physically disconnect the XP drive, boot up and then in Terminal update grub with   sudo update-grub  . If "grub" is on the XP drive I suggest you download the "grub" repair program which should fix it for you which you can get from here [http://sourceforge.net/projects/boot-repair-cd/files/]("http://sourceforge.net/projects/boot-repair-cd/files/")

I know that this might be a bit unclear so please let me know what you do/don't understand so that I can advise further.

---

### Post by oldfred on 2012-02-09
I like Boot-Repair and suggest everyone have it in their tool box.

You can also just install grub to any drive:

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by hbnmgr on 2012-02-09
Thanks Guys - But OldFred ...

What is FDisk?  as in Format Disk?  Fix Disk?
 And is that followed by i or L or 1?

hbnmgr

---

### Post by hbnmgr on 2012-02-09
Just Ran the following ....

> 

Disk identifier: 0x00048095

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   486560654   243280296   83  Linux
/dev/sdb2       486560655   488392064      915705    5  Extended
/dev/sdb5       486560718   488392064      915673+  82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 937 MB, 937649664 bytes
255 heads, 63 sectors/track, 113 cylinders, total 1831347 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x989a85e2

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
stephen@Linus2us:~$ sudo grub-install /dev/sdb
Installation finished. No error reported.



So if no Error Reported, is it safe to unplug my IDE drive with WinXP and use only the SATA drive with Ubuntu?

---

### Post by oldfred on 2012-02-10
In Linux everything is case sensitive, so FDisk does not exist. You can copy & paste commands from here to terminal in a liveCD. Spaces are important also and sometimes it is difficult to tell exact spacing.

```
sudo fdisk -lu
```

If you want to know about a command that you are unsure of use man. fdisk can be used for formating, but the -l (el not 1 or i) is just a list of partitions, u is detail in sectors.

man fdisk

>        -l, --list
              lists the partition table on the specified device and exits.  If
              there  is no device specified, lists the partition tables on all
              detected devices.



---

### Post by hbnmgr on 2012-02-10
After my last Post ... Removed Primary HD, Only Sata drive left, BIOS moved it up to 1st Boot Device, 

and  Behold ... it booted up nice and clean.  WOW ... Too CooLLL.

Thanks Guys!   Will mark Case Closed.

hbnmgr

---

