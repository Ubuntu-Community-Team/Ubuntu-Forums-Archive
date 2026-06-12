---
title: "mount freebsd usf2 as read &amp; write ?"
date: 2011-02-25
forum: General Help
---

### Post by highspider on 2011-02-25
----------------------- /etc/fstab----------------------------------------
# <file system> <mount point>       <type>  <options>                                      <dump>           <pass>
        /dev/sda1                    /media/bsd                                    ufs                 auto,[COLOR=Red]ro[/COLOR],ufstype=ufs2,nodev,nosuid      0    0   

READ ONLY WORKS GREAT
--------------------unmount & try mount 4 read+write--------------------------
umount /bsd
mount -t ufs -o ufstype=ufs2 /dev/sda1 /bsd

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

--the reason ---
"To add the UFS write support to your kernel, uncomment/add the  [COLOR=Red]CONFIG_UFS_FS_WRITE=yes[/COLOR] flag in the config of your kernel, then re-compile  it:"
source [http://ghantoos.org/2009/04/04/mounting-ufs-in-readwrite-under-linux/](http://ghantoos.org/2009/04/04/mounting-ufs-in-readwrite-under-linux/)

#############
# [COLOR=SandyBrown]T[/COLOR][COLOR=DarkSlateGray]H[/COLOR][COLOR=Cyan]E[/COLOR] [COLOR=Silver]Q[/COLOR][COLOR=Cyan]U[/COLOR][COLOR=Yellow]E[/COLOR][COLOR=SeaGreen]S[/COLOR][COLOR=DarkRed]T[/COLOR][COLOR=Silver]I[/COLOR][COLOR=DarkSlateGray]O[/COLOR][COLOR=SeaGreen]N[/COLOR]

 I don't want to have to download the kernel source and uncomment out [COLOR=Red]CONFIG_UFS_FS_WRITE=yes[/COLOR] and build a custom kernel ever time I update the kernel.
Is there a better way? Like when Ubuntu.deb repositories claim a stable kernel is there an auto config script when installing from synaptic -or- aptitude?  Like any way to add this one config opt to .deb kernel W/O building custom one from source?

---

### Post by seawolf167 on 2011-02-25
From what I can tell, Ubuntu has built-in support for UFS[2] read only, so the mount command would go something like this:

```
sudo mkdir /mnt/ufsmountpt
sudo mount -t ufs -r -o ufstype=ufs2 /dev/sdXY /mnt/ufsmountpt
```

where

```
/dev/sdXY
```

is the drive you want to mount

i.e. from 

```
sudo fdisk -l
```

or getting the UUID from 

```
sudo blkid
```

the /etc/fstab entry would then be (or with "UUID=uuid.hex.here" in place of /dev/sdXY)

```
/dev/sdXY   /mnt/ufsmountpt   ufs   auto,ro,ufstype=ufs2,nodev,nosuid    0   0
```

---

### Post by highspider on 2011-02-25
Thank you seawolf167 for responding.  

Sulfurously I've asked 5 question in the last two months and your the only person to respond to any of them.  I was starting to get sucked up inside.

The default support is because of the way the kernel is complied.    The Linux kernel has both read and write support; however, Ubuntu default comply options for the kernel only account for read support.

explains how to get read and WRITE support
[http://ghantoos.org/2009/04/04/mounting-ufs-in-readwrite-under-linux/](http://ghantoos.org/2009/04/04/mounting-ufs-in-readwrite-under-linux/)

*** MY QUESTION
*** I was hoping for a way to automate new kernels to have both read and write support by default.
CONFIG_UFS_FS_WRITE=y*** this way i don't have Manually build the kernel from source every time a stable kernel is released.


There was no UUID for a usf2 drive thats why i didn't a UUID in /etc/fstab
blkid
xxxx@xxx:~$ sudo blkid

/dev/sda1: TYPE="ufs" 
/dev/sda2: UUID="d5dfaca8-18ed-4ef4-8401-1d79b69c719b" TYPE="ext4" 
/dev/sda3: LABEL="XP" UUID="6048050B3B170E89" TYPE="ntfs" 
/dev/sda4: LABEL="Storage" UUID="4E34330D15C87C80" TYPE="ntfs" 


fdisk -l
xxxx@xxx:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa8a8a8a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8600    69079468+  a5  FreeBSD
Partition 1 does not end on cylinder boundary.
/dev/sda2            8601       12036    27599670   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3           12037       15472    27599670    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           15473      121601   852481192+   7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.


yeah i know no swap but have 4g ram thats upgradeable to 16g ram when i get more $
lame windows but like autocad.

---

### Post by seawolf167 on 2011-02-25
> **highspider said:**
> *** MY QUESTION
*** I was hoping for a way to automate new kernels to have both read and write support by default.
CONFIG_UFS_FS_WRITE=y*** this way i don't have Manually build the kernel from source every time a stable kernel is released

I wish I could help with the kernel compilation, maybe someone else around here could help - I'm just finishing up [LFS ]("http://www.linuxfromscratch.org/lfs/")and moving on to [BLFS]("http://www.linuxfromscratch.org/blfs/"), and I don't have a lot of experience compiling kernels.

Good luck!

---

