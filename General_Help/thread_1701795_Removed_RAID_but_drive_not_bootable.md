---
title: "Removed RAID but drive not bootable"
date: 2011-03-06
forum: General Help
---

### Post by quixote on 2011-03-06
I was going to give RAID1 a try, found out I didn't know enough to use it well, and used fdisk to format the drive back to ordinary partitions. Then I was going to zero out the superblocks, and found out I'd done it in the wrong order.  Or something.  Now I have a 2TB brick and need rescuing! :oops:

It's network attached storage drive, an HP Media Vault MV 2120, that runs Uboot for bootloading, and a Debian Lenny OS.  The drive has:
```
sda1:  512MB    /boot   ext2
sda2:  10GB     /       ext3
sda3  extended
sda5  logical   swap
sda6  logical   /home   ext4
```
Both fdisk and Gparted don't report any problems, and the boot sector has a boot flag.

But when I put it back in the HP Media Vault it can't find a boot drive.  The boot and system partitions were rsynced over from a 1TB drive, and that one does boot in the HP Media Vault.

Anybody have any ideas how I can get the 2TB drive back to health??

---

