---
title: "Mount problem with my external hard drive"
date: 2010-04-13
forum: General Help
---

### Post by niksa123 on 2010-04-13
I am currently running ubuntu 9.04 on my hp dv6314tx laptop.
I have a 1 Tb external powered western digital hard drive.

All my 3 partitions are easily mounted as soon as I connect 
my hard disk but then I need to be careful because the
cable connecting the disk to laptop is a bit loose and if I
touch it by mistake the partitions get unmounted and then do not mount again.

If I try to mount using sudo mount -t ntfs /dev/sdb1 /media/sdb1
it says that no such device is present.

I have to reboot and then the partitions are mounted again.
As far as see it some service gets restarted due to reboot and so
the partitions are mounted back. If that is so I guess I can restart the service using sudo service <service> restart.

Can someone tell me what should I do and what is the problem??

---

### Post by darolu on 2010-04-13
The problem probably is that when you (accidentally) unplug the cable, and then re-attach it, your partitions are not assigned to the same /dev/ file but another, after you plug it back run "sudo fdisk -l" to see where they are assigned and use the information to mount them back.

---

### Post by niksa123 on 2010-04-15
This is the output from fdisk after the first time I plugged in my disk. The sdb partitions were automatically mounted.

guest@nikhil-laptop:~$ sudo fdisk -l

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       32635   262140606    7  HPFS/NTFS
/dev/sdb2           32636       77217   358104915    7  HPFS/NTFS
/dev/sdb3           77218      121602   356522049    7  HPFS/NTFS

Now I pulled out the usb cable without unmounting and then inserted the cable, here is the output I got.

guest@nikhil-laptop:~$ sudo fdisk -l

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       32635   262140606    7  HPFS/NTFS
/dev/sdc2           32636       77217   358104915    7  HPFS/NTFS
/dev/sdc3           77218      121602   356522049    7  HPFS/NTFS

guest@nikhil-laptop:~$ sudo mount -t ntfs /dev/sdc1 /media/test/
ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory. Please type '/sbin/mount.ntfs --help' for more information.

sdc1, sdc2, sdc3 are not present in the /dev directory but still fdisk gives the above output. What should I do??

---

