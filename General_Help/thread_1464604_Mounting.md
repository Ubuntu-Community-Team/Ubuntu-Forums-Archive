---
title: "Mounting"
date: 2010-04-28
forum: General Help
---

### Post by ankit.vader on 2010-04-28
My external Hard disk is not mounting automatically, so i tried the manual way, but i'm getting errors. Here's what i did
```

**sudo fdisk -l**

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005d047

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    c  W95 FAT32 (LBA)

```

then i used mount(Directory "Trans" is already there in media)
```

**sudo mount -t vfat /dev/sdb1/ /media/Trans/**
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
this was the output of dmesg
```

**dmesg | tail**
[   73.187655] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   73.187664]  sdb: sdb1
[   73.220758] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   73.220764] sd 3:0:0:0: [sdb] Attached SCSI disk
[  129.817753] FAT: bogus number of reserved sectors
[  129.817764] VFS: Can't find a valid FAT filesystem on dev sdb1.
[  812.295667] FAT: bogus number of reserved sectors
[  812.295679] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 1258.196029] FAT: bogus number of reserved sectors
[ 1258.196041] VFS: Can't find a valid FAT filesystem on dev sdb1.

```
i dont understand why is it not mounting, i also tried using ntfs-3g but that also did'nt work.
Is there something wrong with hard disk. Please help!!

---

### Post by ankit.vader on 2010-04-28
I forgot to mention, it was working fine 10 min earlier, but after i tried to format it using USB startup disk creator, it wasnt mounting thereafter.

---

### Post by Leppie on 2010-04-28
use gparted to format the drive. while you're at it, i would convert the drive to ntfs as fat32 isn't very reliable.

---

### Post by dino99 on 2010-04-28
put the right settings into MountManager ( install it if not yet)

---

### Post by ankit.vader on 2010-04-28
> put the right settings into MountManager ( install it if not yet)
i'm sorry but i'm new to ubuntu. what are the right settings for mount manager, and how do you set them??

---

### Post by ankit.vader on 2010-04-28
i installed mount manager, but disk is still not mounting

---

### Post by jerome1232 on 2010-04-28
So perhaps the format failed. Try reformatting it.

---

### Post by ankit.vader on 2010-04-28
> So perhaps the format failed. Try reformatting it.

disk is not mounting. how can i reformat it. is there a way of reformatting without mounting??

---

### Post by Leppie on 2010-04-28
> **ankit.vader said:**
> disk is not mounting. how can i reformat it. is there a way of reformatting without mounting??
use gparted, to install it:
```
sudo apt-get install gparted
```

---

### Post by mikewhatever on 2010-04-28
> **ankit.vader said:**
> disk is not mounting. how can i reformat it. is there a way of reformatting without mounting??

A partition must be unmounted in order to get formatted, so no problem here.;)

---

