---
title: "help - Second partition is not bootable"
date: 2009-07-09
forum: General Help
---

### Post by ibrabeicker on 2009-07-09
hi all

im new to linux and ubuntu and im having some problems with partitions. Long story short, i've installed ubuntu on a virtual disk inside windows and now i need more space for it, so i created a new partition on my hd using gparted, that was showing as "unallocated" and formated it to ex2 or somethign. 

Then i used LVPM to transfer the content of my virtual disk to the real partition that i've created, but i cant boot from this partition, i got several boot options like Ubuntu 8.04, Ubuntu kernel (recovery), windows xp pro, windows and when i try to boot form the first option, "Ubuntu kernel 9.04" i get

"Error 17: cannot mount partition press any key to continue"

but i cant find the "any" key in my keyboard:lolflag:

this is the result of fdisk -l

[COLOR=DimGray][I]Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x971b971b

Dispositive Boot Start End Blocks Id System
/dev/sda1   *           1       33777   271313721    7  HPFS or NTFS
/dev/sda2           33778       38913    41254920   83  Linux[/I][/COLOR]

sda1 is where my original ubuntu is installed on the virtual disk alongside with windows and sda 2 is the partition that i created and copied and that doesnt work

**so i need help making the second partition bootable** so i can remove the virtual disk from windows

---

### Post by az on 2009-07-09
I think this will help:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

You do not need to make the partition bootable insofar as the partition table is concerned.  The "boot" flag in the partition table is meant to let you boot from a partition that is not the first partition on the drive, so setting the "boot" flag on more than one partition is not any use.

But Grub takes care of booting your OSes.

---

