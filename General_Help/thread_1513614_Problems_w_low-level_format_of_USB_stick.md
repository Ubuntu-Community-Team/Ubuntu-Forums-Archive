---
title: "Problems w/ low-level format of USB stick"
date: 2010-06-19
forum: General Help
---

### Post by nathan28 on 2010-06-19
I have a Kingston Datatraveller 150 32gb that I've had intermittent problems with mounting in ubuntu 8.x, XP and Vista. I.e., it's unreliable. I managed to completely brick it by dropping it on a magnet at work, so I figured I'd just reformat it completely.

I'm using 10.04 x64 right now and want to do this from the command line, not with some 3rd party program on XP.

Well...

> ~$ mkfs -t fat32 -V /dev/sdb
mkfs (util-linux-ng 2.17.2)
mkfs.fat32 /dev/sdb 
mkfs.fat32: No such file or directory

~$ sudo dd if=/dev/zero of=dev/sdb
dd: opening `dev/sdb': No such file or directory


Here's disk utility, which says the disk is /dev/sdb.

> Error creating partition table: helper exited with exit code 1: cannot open /dev/sdb: No medium found

dmesg |grep -i usb  doesn't show a sdb device, but one does show up in /dev if I do a ls.

> [  362.741840] usb-storage: device found at 3
[  362.741844] usb-storage: waiting for device to settle before scanning
[  367.743127] usb-storage: device scan complete
[  367.803224] scsi 7:0:0:0: Direct-Access              USB DISK 30X     1.00 PQ: 0 ANSI: 0 CCS
[  378.150199] usb 2-1: USB disconnect, address 3


I know that Kingston disks have compatibility issues, a lot of them are pirate clones and that they generally suck, but I could use 32 more gb of storage that used to have.

pls halp

---

### Post by Sammi on 2010-06-19
sudo apt-get install gparted

Use that.

---

### Post by efflandt on 2010-06-19
The reason the following failed is because you forgot the root path (should have been /dev/sdb):

```
~$ sudo dd if=/dev/zero of=dev/sdb
dd: opening `dev/sdb': No such file or directory                      
```Note that you cannot format a drive like a floppy.  You have to create a partition on it first.  But you may have mangled the partition table.

So like the other post says, install gparted.  Then create an msdos partition table on /dev/sdb, then create primary partition /dev/sdb1 with whatever partition type you want.

---

### Post by nathan28 on 2010-06-19
> **efflandt said:**
> The reason the following failed is because you forgot the root path (should have been /dev/sdb):

```
~$ sudo dd if=/dev/zero of=dev/sdb
dd: opening `dev/sdb': No such file or directory                      
```Note that you cannot format a drive like a floppy.  You have to create a partition on it first.  But you may have mangled the partition table.

So like the other post says, install gparted.  Then create an msdos partition table on /dev/sdb, then create primary partition /dev/sdb1 with whatever partition type you want.


Thanks, my "adult add" got in the way of the root... it still can't find the drive. Gparted doesn't show it, either, even with a sudo gparted /dev/sdb... going to try a parted magic boot CD.

on edit partition magic can't find it, either. it isn't listed in /media, gparted still doesn't see it.

---

