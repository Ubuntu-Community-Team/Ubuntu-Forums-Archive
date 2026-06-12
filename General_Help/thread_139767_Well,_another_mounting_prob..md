---
title: "Well, another mounting prob."
date: 2006-03-04
forum: General Help
---

### Post by xumium on 2006-03-04
Dear Forumers,

Sorry for another one of these posts, I just couldn't find a solution to my problem.

So, I decided to mount my NTFS partition according to the FAQ, followed everything as aid and now my fstab looks like this:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/windows ntfs ro,nls=utf8,umask=0222 0 0


kinda lovely ain't it?
then when I try to umount, all i get is
> 
xumium@MAIN:~$ sudo umount -a
umount: /dev: device is busy
umount: /: device is busy


now to the additonal info, my partition table looks like this:

> 
Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9247    74269408+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2            9247        9976     5859375   83  Linux
/dev/hda3            9977       10011      281137+   5  Extended
/dev/hda5            9977       10011      281106   82  Linux swap / Solaris


---

### Post by hove99 on 2006-03-04
I usually get this error, if I have a nautilus or other window/application open, which uses/reads the drive. If you don't see anything, maybe try the system monitor to find processes?

Regards

---

