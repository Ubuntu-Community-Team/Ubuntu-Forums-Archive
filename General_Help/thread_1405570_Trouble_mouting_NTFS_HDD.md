---
title: "Trouble mouting NTFS HDD"
date: 2010-02-12
forum: General Help
---

### Post by xValo87x on 2010-02-12
Disk utility picks up all my HDD's and Ubuntu will auto-mount my Windows HDD just fine when clicking on it.

The problem is I want my Data Drive mounted so I can access all of my Music, Videos, and Programs on it.

ntfs-3g is pre-installed with 9.10 so I used this process to try and mount my drive but with no avail:
```

sudo /bin/bash
mkdir /media/windisk

```

Then attempting the mount:
```

sudo mount -t ntfs-3g /dev/sdc1 /media/windisk
ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

```

Looking at sudo fdisk -l:
```

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf1e545f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       91202   732571648    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13480e78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       38914   312466432    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdc: 750.2 GB, 750156374016 bytes  <--Data Drive
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1 <---correct path              1       91202   732571648    7  HPFS/NTFS  <--NTFS

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b972c4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       23330   187398193+  83  Linux
/dev/sdd2           23331       24321     7960207+   5  Extended
/dev/sdd5           23331       24321     7960176   82  Linux swap / Solaris

```

I'm lost as to what could be going on. If anyone could offer any assistance I would be most grateful.

--Valo

---

### Post by samantha_ on 2010-02-12
> **xValo87x said:**
> Disk utility picks up all my HDD's and Ubuntu will auto-mount my Windows HDD just fine when clicking on it.

The problem is I want my Data Drive mounted so I can access all of my Music, Videos, and Programs on it.

ntfs-3g is pre-installed with 9.10 so I used this process to try and mount my drive but with no avail:
```

sudo /bin/bash
mkdir /media/windisk

```

Then attempting the mount:
```

sudo mount -t ntfs-3g /dev/sdc1 /media/windisk
ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

```

Looking at sudo fdisk -l:
```

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf1e545f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       91202   732571648    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13480e78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       38914   312466432    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdc: 750.2 GB, 750156374016 bytes  <--Data Drive
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1 <---correct path              1       91202   732571648    7  HPFS/NTFS  <--NTFS

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b972c4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       23330   187398193+  83  Linux
/dev/sdd2           23331       24321     7960207+   5  Extended
/dev/sdd5           23331       24321     7960176   82  Linux swap / Solaris

```

I'm lost as to what could be going on. If anyone could offer any assistance I would be most grateful.

--Valo
theirs only one partition on that drive, so
```

sudo mount -t ntfs-3g /dev/sdc /media/windisk

```

---

### Post by xValo87x on 2010-02-12
That's the first thing I tried and I got this error:
```

root@valo-desktop:~# sudo mount -t ntfs-3g /dev/sdc /media/windisk
NTFS signature is missing.
Failed to mount '/dev/sdc': Invalid argument
The device '/dev/sdc' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@valo-desktop:~# 

```

So I tried /dev/sdc1

fdisk records /dev/sdc as NTFS though; So..

---

### Post by xValo87x on 2010-02-12
Bump, Any Idea's?  I've been struggling for the last hour with no luck.

The drive works fine in Win7 and registers as NTFS in Win7+fdisk.

---

### Post by Camaguey on 2010-02-14
Did you unmount and "safely remove" it from Windows 7 before trying to mount it on linux?
Also,
> **carlee said:**
> ```

sudo mkdir /media/external
sudo mount -t ntfs-3g /dev/sdb1 /media/external -o force
```

---

