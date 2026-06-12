---
title: "kubuntu not reconizing external hardrive and usb flash drive"
date: 2006-05-27
forum: General Help
---

### Post by mrvgarg on 2006-05-27
Hi

I have jusj installed kubuntu breezy but it will not reconize external hardrive and usb flash drive. Please help. The external hardrive is FAT32.

---

### Post by Sutekh on 2006-05-27
This link should help you get access to your Windows formatted (FAT) partitions

[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

### Post by mrvgarg on 2006-05-28
I keep getting this:

An error occurred while loading media:/sda1:
The file or folder media:/sda1 does not exist.

---

### Post by Sutekh on 2006-05-28
Can you provide the information on your partitions?
```
sudo fdisk -l
```
and your mounting configuration?
```
cat /etc/fstab
```

---

### Post by mrvgarg on 2006-05-28
With external hardrive turned off:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4676    37559938+  83  Linux
/dev/hda2            4677        4864     1510110    5  Extended
/dev/hda5            4677        4864     1510078+  82  Linux swap / Solaris


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


With external hardrive on:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4676    37559938+  83  Linux
/dev/hda2            4677        4864     1510110    5  Extended
/dev/hda5            4677        4864     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401    c  W95 FAT32 (LBA)


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Sutekh on 2006-05-28
Okay, could you edit your /etc/fstab to include an extra line for the external drive?

First create a folder to 'mount' the partition to
```
sudo mkdir /mnt/usbdrive
``` You can use any folder you like, I'll use /mnt/usbdrive for this example

Use these commands to copy the file and edit it using **nan**o.  You could use gedit if you are more comfortable with that
```
sudo cp /etc/fstab /etc/fstab_backup
sudo **nano** /etc/fstab
``` The line you should add is this
```
/dev/sda1   /mnt/usbdrive   vfat   iocharset=utf8,umask=0000   0   0
``` Save the file (Ctrl +O if you use nano) and exit (Ctrl + X).  The mount the 
drive using
```
sudo mount /mnt/usbdrive
```

---

### Post by mrvgarg on 2006-05-29
Thank You So Much

---

### Post by Sutekh on 2006-05-29
[quote=mrvgarg]Thank You So Much[/quote]Glad it worked out alright.

There are other options that you might want to look into.  The **user** option allows an ordinary user to mount the drive (no need for sudo).  The **noauto** stops the drive being mounted at startup.  There are more.  Check out
```
man mount
```for the manual or this link

[Mount Man Page](http://www.die.net/doc/linux/man/man8/mount.8.html)

```

/dev/sda1   /mnt/usbdrive   vfat   **user,noauto**,iocharset=utf8,umask=0000   0   0
```

---

### Post by mrvgarg on 2006-05-30
Thanks again. However the disk keeps spinning but in windows it didnt.

---

### Post by Kietedan on 2008-05-27
I'm having almost the same issue, save that the usb external drive doesn't even show up when I run fdisk.

with the TB external USB on and off fdisk looks like the following:

[INDENT]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31b931b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13721371

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16981698

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        6994    56179273+  83  Linux
/dev/sdc2            6995        7297     2433847+   5  Extended
/dev/sdc5            6995        7297     2433816   82  Linux swap / Solaris[/INDENT]

and cat /etc/fstab looks like this:

[INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=8b7fb753-e3a9-4bcf-bce4-8579def78e89 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hdb5
UUID=3ff47fa2-8262-4eb8-b947-83faf386ceb3 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/INDENT]

Does any one know how I can fix this?

---

