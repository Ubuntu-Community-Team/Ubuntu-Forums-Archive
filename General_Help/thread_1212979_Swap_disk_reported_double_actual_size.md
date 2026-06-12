---
title: "Swap disk reported double actual size"
date: 2009-07-14
forum: General Help
---

### Post by itsjareds on 2009-07-14
[SIZE="4"]**Solved, see this post:**[/SIZE]
[http://ubuntuforums.org/showthread.php?p=7614668#post7614668]("http://ubuntuforums.org/showthread.php?p=7614668#post7614668")
-------------
Hi, I just had to change my swap's UUID in /etc/fstab after I resized my swap partition. Everything works great but when I open the system monitor (gnome-system-monitor), the swap is reported to be 546.3MB. My swap partition is only 300MB large.

Why do I have extra swap? I only have one swap partition. I don't know where this extra swap is coming from.

Here's some info:

fdisk -l
```
jared@jared-desktop:~$ fdisk -l

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3938    31631953+   7  HPFS/NTFS
/dev/sda2            3939        7008    24659775    7  HPFS/NTFS
/dev/sda3            7009        9692    21559230   83  Linux
/dev/sda4            9693        9730      305235    5  Extended
/dev/sda5            9693        9730      305203+  83  Linux
```

/etc/fstab
```
jared@jared-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/sda3 during installation
UUID=c15c3c00-e0d8-4b70-a075-41af9986e6b8 /               ext3    relatime,errors=remount-ro 0       1

# swap was on /dev/sda5 during installation
#UUID=ca0db2c3-4f2f-412a-9f81-67e284d5a5a4 none            swap    sw              0       0
UUID=b2c59c0d-1396-4355-ba8e-cb6fa53a8447 none            swap    sw              0       0

/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

# Windows partitions
/dev/sda2 /media/win7 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda1 /media/winxp ntfs-3g defaults,locale=en_US.utf8 0 0
```

---

### Post by itsjareds on 2009-07-14
Hmm.. it may have to do with this ramzswap0. I don't know how to remove it.

```
jared@jared-desktop:~$ cat /proc/partitions
major minor  #blocks  name

   8        0   78156288 sda
   8        1   31631953 sda1
   8        2   24659775 sda2
   8        3   21559230 sda3
   8        4          1 sda4
   8        5     305203 sda5
 251        0     254272 ramzswap0

```

---

### Post by itsjareds on 2009-07-14
Nevermind.. found the answer.

[http://ubuntuforums.org/showthread.php?p=7268741]("http://ubuntuforums.org/showthread.php?p=7268741")

Apparently there is a bug that Ubuntu does not remove some virtual swap files when you install from the LiveCD. Here's the fix:

```

sudo rm /usr/share/initramfs-tools/conf.d/compcache
sudo update-initramfs -u

```

Then reboot. Everything should be fine.

[solved]

---

