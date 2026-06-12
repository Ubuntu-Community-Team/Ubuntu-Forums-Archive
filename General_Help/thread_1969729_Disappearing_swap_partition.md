---
title: "Disappearing swap partition"
date: 2012-04-30
forum: General Help
---

### Post by scj1091 on 2012-04-30
I'd been running Ubuntu on Windows in VirtualBox but when Precise was  released I decided to dual boot. I shrank my Windows partition and  installed Ubuntu after it, during installation my partition layout was  something like this:
#1 NTFS hidden OEM Recovery ~ 10GB
#2 NTFS Windows 7 ~312GB boot
#3 Ext4 Ubuntu ~50GB
#5 Logical linux-swap ~2GB

Problem is that my swap partition keeps disappearing. I ran gparted to  mark my Windows partition as boot so that hibernation will work and  noticed an error on the swap partition (unknown / unable to detect filesystem). Parted shows a 2GB  logical partition with no fs. Blkid doesn't show anything for /dev/sda5  and swapon -s indicates only cryptswap exists. Deleted the swap  partition, recreated it, rebooted. Blkid gave me the UUID which I  updated in fstab, but when I rebooted the partition was giving errors  again. fdisk -l /dev/sda shows the correct partition table but  parted/gparted/blkid still can't see the swap. Any thoughts?

---

### Post by scj1091 on 2012-05-15
Bump. Anyone have any thoughts? I could just delete the swap partition and use a swap file, but I'd like to know *why *it wasn't working.

---

### Post by JC Cheloven on 2012-05-15
Hi, 

Although you seem to know your way around among system files etc, could you please copy-paste the output of some? Perhaps we could see something that passed unnoticed to you. In particular the output of
```
sudo fdisk -l
sudo blkid
cat /etc/fstab

```

Side note 1: your 10Gb recovery patition may (likely) have become unusable, despite an entry in grub for it. It happened to me too many times.

Side note 2: I always installed in logical partitions both Ubuntu and swap, but I don't think that really matters, [COLOR="Red"]as long as there is NOT any other unnoticed primary partition[/COLOR] (you know, 4 maximun).

---

### Post by scj1091 on 2012-05-15
Well, the OEM recovery partition is fine because I reinstalled Windows from it a few months ago. And here's what I got:
```

:~$ sudo fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcdc555a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    21757951    10877952   27  Hidden NTFS WinRE
/dev/sda2   *    21757952   676564991   327403520    7  HPFS/NTFS/exFAT
/dev/sda3       676564992   777541631    50488320   83  Linux
/dev/sda4       777543678   781422591     1939457    5  Extended
/dev/sda5       777545728   781422591     1938432   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 1984 MB, 1984954368 bytes
255 heads, 63 sectors/track, 241 cylinders, total 3876864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc0dad479

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

:~$ sudo blkid
/dev/sda1: LABEL="Recovery" UUID="02B8260FB8260231" TYPE="ntfs" 
/dev/sda2: UUID="1042782A42781726" TYPE="ntfs" 
/dev/sda3: UUID="1ae56cfd-9100-44c3-abe2-ce8c01d25096" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="8fb7a344-1d87-4487-8858-efaead23da54" TYPE="swap"

:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=1ae56cfd-9100-44c3-abe2-ce8c01d25096 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=ee5904b9-972a-4840-820f-b1a117752d39 none swap sw  0       0
/dev/mapper/cryptswap1 none     swap    sw              0       0
```And of course, now blkid can see cryptswap, because why not. Does the above look right or is something funky going on?

---

### Post by wilee-nilee on 2012-05-15
never mind

---

### Post by oldfred on 2012-05-15
If it is encrypted then gparted cannot see the file system, so that is correct. Otherwise it would not be encrypted.

Everything looks ok, does it all work ok? Is so then it should be fine.

---

