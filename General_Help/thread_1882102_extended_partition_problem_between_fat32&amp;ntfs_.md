---
title: "extended partition problem between fat32&amp;ntfs partitions"
date: 2011-11-16
forum: General Help
---

### Post by numberg on 2011-11-16
hi people from my first thread/message! =) i normally deal problems by my own .. but kinda stuck with this one .. did search 'the web' ..

the disk is an external hd (yumi installed in fat32 and ubuntu 11.10 in ext4) .. below is the default partition configuration:

sda1 fat32 yumi
sda2 ext4 / ubuntu 11.10
unallocated
sda3 ntfs

i use live cd to create logical parts (ext4 and swap) in extended from unallocated space .. after applying the new cfg (by using gparted) i can mount and use all of the partitions as it should be .. below the new cfg:

sda1 fat32 yumi
sda2 ext4 / ubuntu 11.10
sda4 extended part.
|- sda5 ext4
|- sda6 swap
sda3 ntfs

but if i boot in to ubuntu (sda2) the first logical (sda5 ext4) just collapses .. i can see sda5 part. in nautilus but gparted shows it as unknown (unformatted) .. and if i try to mount/delete/check that part. it says 'disk/part. is busy' ...

and i am sure it is always the first 'logical' cause i use different partition cfgs, like this one here:

sda1 fat32 yumi
 sda2 ext4 / ubuntu 11.10
sda4 ext4
sda5 extended part.
 |- sda6 ext4
 |- sda7 swap
|- sda3 ntfs

in this example it is sda6 ext4 (not sda4 ext4) which breaks either after booting in to ubuntu ..

i do check all partitions after i create the new part. which says nothing .. so any ideas?

edit: i forgot to mention that i even tried to leave some space between primary part. and extended part. .. cause i thought that ubuntu might doin something weird to the end of its own part. while booting .. if i remember correctly extended part. table placed on the start of itself .. didnt work either .. the cfg looks like below:

sda1 fat32 yumi
 sda2 ext4 / ubuntu 11.10
sda4 ext4
unallocated space (around 100-200 mb not remembering exactly)
sda5 extended part.
 |- sda6 ext4
 |- sda7 swap
|- sda3 ntfs

---

### Post by Cyclane on 2011-11-16
Strange problem your describing.

First of all could you post the output of 'sudo fdisk -l'. I see you've taken great care noting everything down but fdisk might be a little clearer for us.

```
sudo fdisk -l
```

##EDIT:
I'm not sure if this will work, I can't test it because I'm on a LVM partition and that's a little different.

When Ubuntu, denies to mount the partition could you run the following command:```
sudo lsof /dev/sdaX
```
/dev/sdaX being the partition you're trying to mount.

---

### Post by numberg on 2011-11-16
ups i should have thought that sorry .. tnx by the way ..

here it is:
[HTML]
sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
64 heads, 12 sectors/track, 305262 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x09fa04f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *    10242048   144760831    67259392    7  HPFS/NTFS/exFAT
/dev/sda3       144760832   234438655    44838912    f  W95 Ext'd (LBA)
/dev/sda5       144762880   234438655    44837888    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 750.2 GB, 750153367552 bytes
255 heads, 63 sectors/track, 91200 cylinders, total 1465143296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1a8e523b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    67103504    33550728+   c  W95 FAT32 (LBA)
/dev/sdb2        67104768   134213631    33554432   83  Linux
/dev/sdb3       134464050   201567554    33551752+  83  Linux
/dev/sdb4       201570304  1465127999   631778848    f  W95 Ext'd (LBA)
/dev/sdb5       201572352   268681215    33554432   83  Linux
/dev/sdb6       268683264   272879615     2098176   82  Linux swap / Solaris
/dev/sdb7       272880153  1465127999   596123923+   7  HPFS/NTFS/exFAT[/HTML]and the other:
[HTML]
sudo lsof /dev/sdb5

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/kep/.gvfs
      Output information may be incomplete.[/HTML]when i use it without sudo it returns nothing .. and result is same with other working partitions ..

---

### Post by JKyleOKC on 2011-11-16
Your original message shows that you created the extended partition as /dev/sda5 but the fdisk output shows it as /dev/sda3 -- and doesn't show /dev/sda1 at all.

This leads me to believe that something about the partition table on /dev/sda is confusing the software considerably.

An extended partition should NEVER be identified as /dev/sda5; it must be in one of the four primary slots of the table, and thus cannot have a number greater than 4. Most of the time, it gets defined as /dev/sda4 but sometimes it can be sda3 and I've even seen it as sda2 (but only rarely).

It's possible that putting the extended partition between two primary partitions might be causing the problem, but it's also possible that differences between the boot-up partition discovery procedures between the Live CD and your sda2 installation might be doing it.

There's a "testdisk" package in the repositories that you can use to inspect the partition table, without making any changes to it unless you explicitly tell it to do so. This might help trace down what's going wrong...

---

### Post by numberg on 2011-11-17
jim, first of all tnx for your respond .. while writing my first post i assumed that there is only one disk (external) and therefore disk is named as sda .. and as you can see; fdisk output does not return any linux file system (exts) partitioned in sda .. that one is internal disk (has vista in it) .. the problematic disk in fdisk output named as sdb .. i should've mentioned that .. my mistake sorry ..


"An extended partition should NEVER be identified as /dev/sda5" i've never thought/heard this before actually .. but my first cfg from first post was:

sda1 fat32 yumi
sda2 ext4 / ubuntu 11.10
sda4 extended part.
|- sda5 ext4
|- sda6 swap
sda3 ntfs

which actually fits the limit well you mentioned .. didn't work ..

"It's possible that putting the extended partition between two primary partitions might be causing the problem." one of the cfg i've tried was:

sda1 fat32 yumi
sda2 ext4 / ubuntu 11.10
sda4 ext4
sda5 extended part.
|- sda6 ext4
|- sda7 swap
|- sda3 ntfs

in this example extended part. is the last part ..

well i will definitely try testdisk if backing up fat32 part, deleting and restoring it  won't solve the prolem .. to actually spend time probing whole disk with testdisk, i wanna try this first ..

---

### Post by efflandt on 2011-11-17
It is still confusing that you keep referring to sda when your Linux partitions according to fdisk are on sdb (unless you changed that now). So it is possible that you are attempting to mount a partition from the wrong drive as a wrong type.

Note that changing boot order in BIOS to boot from the 750 GB drive does NOT make that drive sda.  For example I am currently booting 11.10 on sdb1 from grub2 on sdb (an SSD drive) and fdisk (or gparted) shows the boot drive as sdb.

Which drive is which is determined by which cable plug is connected to which drive (if plugs are marked A and B or 1 and 2), or for older drives with unmarked plugs by master/slave drive jumper settings.

---

### Post by numberg on 2011-11-17
disk i am trying to partition is an external usb harddisk as i have mentioned before .. so when i plug it into a pc which does not have any other disk it is sda .. if there is an internal disk it becomes sdb like shown below:

sdb1 fat32 yumi
sdb2 ext4 / ubuntu 11.10
sdb4 extended part.
|- sdb5 ext4
|- sdb6 swap
sdb3 ntfs

and i know that while in bootloader prompt it is sda (hd0 for grub or syslinux to be exact) and after booting kernel it becomes sdb (if of course there is an internal drive) .. so disk does not plugged with ide/sata cables .. it is just plain old usb 2.0 ..

edit: so far i have delete, create and restore fat32 .. didn't work .. next step testdisk .. if it won't work will backup everything, delete all parts and apply this config by only using gparted:

sdb1 fat32 yumi
sdb2 ntfs
sdb3 ext4 / ubuntu 11.10
sdb4 extended part.
|- sdb5 ext4
|- sdb6 swap

that should work i hope .. will update thread with result ..

---

### Post by numberg on 2011-11-19
here is the update:
i did try testdisk and it did fix the troubled partition .. but after booting back in to ubuntu, the partition was scrambled again .. then i did back up whole disk, delete all partitions, recreate mbr and partitions and then voila! everything works just fine as it supposed to be ..


the partition cfg below definitely works without any problem:

sda1 fat32 yumi
sda2 ext4 / ubuntu 11.10
sda4 extended part.
|- sda5 ext4
|- sda6 swap
sda3 ntfs

i still have no idea what was the problem .. can only guess there was something wrong with mbr, cause i did delete and recreate every partition without touching mbr before deleting whole mbr and partition table .. my pc at work actually has a more complicated partition config than this .. tnx anyways ..

---

