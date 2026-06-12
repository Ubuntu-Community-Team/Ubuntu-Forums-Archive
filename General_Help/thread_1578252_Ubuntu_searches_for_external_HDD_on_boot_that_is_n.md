---
title: "Ubuntu searches for external HDD on boot that is not plugged in"
date: 2010-09-20
forum: General Help
---

### Post by lotec on 2010-09-20
Hi guys,

As per the title, whenever Ubuntu boots, it searches for an external hard drive that I no longer have plugged in. It hangs on the Ubuntu load screen for a while, then says that it cannot find the drive and I have to press (S) to skip the attempt.

Any ideas? I did a google search, but couldn't seem to come up with anything.

Thanks guys.

---

### Post by matthewbpt on 2010-09-20
You probably have an fstab entry for the drive. fstab is a file which lists partitions to mount on startup. Go into a terminal and type
```
sudo fdisk -l
```
and
```
cat /etc/fstab
```
And post the output of each here. We should be able to tell you if fstab has an entry for an external drive.

---

### Post by lotec on 2010-09-20
> **matthewbpt said:**
> You probably have an fstab entry for the drive. fstab is a file which lists partitions to mount on startup. Go into a terminal and type
```
sudo fdisk -l
```
and
```
cat /etc/fstab
```
And post the output of each here. We should be able to tell you if fstab has an entry for an external drive.

Hi Matt,

```
sudo fdisk -l
```

produces 

> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf2fa3d41

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6619    53057536    7  HPFS/NTFS
/dev/sda3            6620       11473    38989755    5  Extended
/dev/sda4           11474       38914   220409856    7  HPFS/NTFS
/dev/sda5            6620       11473    38989723+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a1649

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182402  1465137560    7  HPFS/NTFS


None of the drives listed above is the drive I am talking about.

```
cat /etc/fstab
```

produces

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sdc1 :
UUID=42DC4CB4DC4CA44F	/media/Elements_	ntfs-3g	defaults,nosuid,nodev,locale=en_AU.utf8	0	0
#Entry for /dev/sda4 :
UUID=DE1841A81841808F	/media/M1330_Storage	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda1 :
UUID=20AAD444AAD417DC	/media/System_Reserved	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda2 :
UUID=9612F20312F1E85F	/media/asdf	ntfs	defaults,nls=utf8,umask=0222	00
#Entry for /dev/sdb1 :
UUID=46A2CC8CA2CC81C3	/media/movies	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077	0	0
UUID=6CAE6FEDAE6FAE70	/media/Storage_	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0

#UUID=188ce452-3091-4cd7-a351-1cdbe50ec148	/	ext4	errors=remount-ro	0	1


The drive that is causing the issue is the "Storage_".

Off to a good start!

---

### Post by matthewbpt on 2010-09-20
That does help indeed, what youwant to do is edit fstab

```
sudo nano /etc/fstab
```

replace this line

```
UUID=6CAE6FEDAE6FAE70	/media/Storage_	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid= 1000,dmask=0077	0	0
```
with
```
UUID=6CAE6FEDAE6FAE70	/media/Storage_	ntfs	defaults,noauto,nosuid,nodev,uhelper=udisks,uid=1000,gid= 1000,dmask=0077	0	0
```

Then press Ctrl+x to save the changes and exit.

Basically you're adding the "noauto" option, so that partition is not automounted. If this doesnt work then what you can do is add a # infront of that line to comment out the entry completely.

Hope this helps

---

### Post by lotec on 2010-09-20
> **matthewbpt said:**
> That does help indeed, what youwant to do is edit fstab

```
sudo nano /etc/fstab
```

replace this line

```
UUID=6CAE6FEDAE6FAE70	/media/Storage_	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid= 1000,dmask=0077	0	0
```
with
```
UUID=6CAE6FEDAE6FAE70	/media/Storage_	ntfs	defaults,noauto,nosuid,nodev,uhelper=udisks,uid=1000,gid= 1000,dmask=0077	0	0
```

Then press Ctrl+x to save the changes and exit.

Basically you're adding the "noauto" option, so that partition is not automounted. If this doesnt work then what you can do is add a # infront of that line to comment out the entry completely.

Hope this helps

Hey mate, 

Worked great. Thanks heaps!

---

