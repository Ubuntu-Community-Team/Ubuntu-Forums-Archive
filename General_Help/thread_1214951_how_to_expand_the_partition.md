---
title: "how to expand the partition?"
date: 2009-07-16
forum: General Help
---

### Post by manij on 2009-07-16
I restored my "Hardy" installation to a new hard drive using partimage. every thing works fine, except for one small issue.

The original partition was 22g, the new on is 35. But it still reads as 22 G, how do I fix this issue. I used live CD and it says the partition is 35G. Please help.

---

### Post by michy99 on 2009-07-16
What is the output of these commands?```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Finalfantasykid on 2009-07-16
I had this problem too, but I was able to fix it by booting the live cd, and loading up GParted.  Then I selected the linux partition, and I selected 'check'.  That seemed to fix it for me.

---

### Post by bodhi.zazen on 2009-07-16
> **manij said:**
> I restored my "Hardy" installation to a new hard drive using partimage. every thing works fine, except for one small issue.

The original partition was 22g, the new on is 35. But it still reads as 22 G, how do I fix this issue. I used live CD and it says the partition is 35G. Please help.

Depends on the underlying file system.

See :

[How to: Resize an Encrypted Partition (LUKS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=4530641") 

From a live CD, assuming ext2/3 (not sure about 4, have not tried)

```
sudo e2fsck -f /dev/sdxy[FONT=monospace]
[/FONT]sudo resize2fs -p /dev/mapper/sdxy
```

Where "sdxy" is your partition.

---

### Post by manij on 2009-07-16
> **michy99 said:**
> What is the output of these commands?```
sudo fdisk -l
cat /etc/fstab
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         640     5140768+   7  HPFS/NTFS
/dev/sda2            1584       38913   299853225    5  Extended
/dev/sda5            1585        5607    32314747+  83  Linux
/dev/sda6            5608        5899     2345458+  82  Linux swap / Solaris
/dev/sda7            5900       10274    35142156   83  Linux
/dev/sda8           10275       38913   230042736    b  W95 FAT32

SDA7 is the partition i'm concerned about


here is the cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=72044420-514e-4c05-a2d4-87ede51f8f3c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=33dec139-1119-4022-9b26-76a74c797374 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

---

### Post by manij on 2009-07-16
Solved! Checked with Gparted. that fixed it

Thanks

---

