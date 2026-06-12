---
title: "don't want to enter password when opening partion"
date: 2010-05-22
forum: General Help
---

### Post by keevill on 2010-05-22
I have a laptop with 2 partitions . The second partition is called 'Data' and is for storing files. Every time I want to access it, I have to enter the root password. This is not a big deal but its tiresome when trying to run a program like Picasa. The folders where the pictures are located are in the data partition and if I forget to mount the partition, then the folders are not accessed under Picasa.
How can I avoid entering the password every time. The data partition would be better opened automatically when the laptop boots up.
-keevill-

---

### Post by yabbadabbadont on 2010-05-22
Please post the contents of the /etc/fstab file.

---

### Post by keevill on 2010-05-22
> **yabbadabbadont said:**
> Please post the contents of the /etc/fstab file.

wow ! that was quick 
________

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                               0  0  
# / was on /dev/sda1 during installation
UUID=2c11c4ed-6c5c-4e5c-8767-30dac980e405  /              ext2         relatime,errors=remount-ro             0  1  
# swap was on /dev/sda5 during installation
UUID=918c8a62-eb93-4f42-93b0-de940fabd9eb  none           swap         sw                                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                  0  0  
# For USB access with Virtualbox
none                                       /proc/bus/usb  usbfs        devgid=124,devmode=664                 0  0  
/dev/sda2                                  /media/sda2    ntfs         nls=iso8859-1,ro,users,umask=000,user  0  0

---

### Post by yabbadabbadont on 2010-05-22
Open a terminal window and please list the output of:
```
ls -l /dev/disk/by-label
```
and
```
sudo fdisk -l
```

---

### Post by NTHQ on 2010-05-22
You can set the partition to mount automatically at start up.

[This thread]("http://ubuntuforums.org/showthread.php?t=785263&highlight=automatically+mount+partition") explains how to do it with an NTFS partition.

---

### Post by keevill on 2010-05-22
> **yabbadabbadont said:**
> Open a terminal window and please list the output of:
```
ls -l /dev/disk/by-label
```

total 0
lrwxrwxrwx 1 root root 10 May 23 02:10 NO_NAME -> ../../sdb1
lrwxrwxrwx 1 root root 10 May 23  2010 data -> ../../sda5


and
```
sudo fdisk -l
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68274ead

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4400    35341976   83  Linux
/dev/sda3            4401       14593    81875272+   5  Extended
/dev/sda5            4401       14593    81875241   83  Linux

---

### Post by keevill on 2010-05-22
> **NTHQ said:**
> You can set the partition to mount automatically at start up.

[This thread]("http://ubuntuforums.org/showthread.php?t=785263&highlight=automatically+mount+partition") explains how to do it with an NTFS partition.

I followed these instructions but when the machine starts up, there is a verbose error message and the drive is not mounted. I have to manually mount it after inputting the password.
-keevill-

---

### Post by mharrison on 2010-05-22
Do you have ntfs-3g installed?

Do this...

```

sudo apt-get install ntfs-3g

```
```

sudo mkdir /media/[insert name here]

```
```
sudo fdisk -l
```
```
sudo gedit /etc/fstab
```

My fstab entry looks like this:
/dev/sdb1	/media/Backup	ntfs-3g	defaults	0	0

Where /dev/sdb1 was the name you got from the fdisk command and the /media/Backup is what you named the directory you created.

Hope this helps.  

FYI.....one time I had the device names change on me and the drives not mount, but redoing the last 2 code blocks fixed it..

---

### Post by keevill on 2010-05-23
> **mharrison said:**
> Do you have ntfs-3g installed?

Do this...

```

sudo apt-get install ntfs-3g

```
```

sudo mkdir /media/[insert name here]

```
```
sudo fdisk -l
```
```
sudo gedit /etc/fstab
```

My fstab entry looks like this:
/dev/sdb1	/media/Backup	ntfs-3g	defaults	0	0

Where /dev/sdb1 was the name you got from the fdisk command and the /media/Backup is what you named the directory you created.

Hope this helps.  

FYI.....one time I had the device names change on me and the drives not mount, but redoing the last 2 code blocks fixed it..

My fstab entry looks like this.

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=2c11c4ed-6c5c-4e5c-8767-30dac980e405 / ext2 relatime,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=918c8a62-eb93-4f42-93b0-de940fabd9eb none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0
/dev/sda2 /media/sda2 ntfs-3g defaults,locale=(null) 0 0

-keevill-

---

