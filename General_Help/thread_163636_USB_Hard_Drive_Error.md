---
title: "USB Hard Drive Error"
date: 2006-04-21
forum: General Help
---

### Post by jonnymccullagh on 2006-04-21
When I plug an external USB hard drive in I get a Konqueror window with an address:
media:/sda1
Which gives an error: 
An error occurred while loading media:/sda1:
The file or folder media:/sda1 does not exist.

I'm pretty sure this did work when I originally started kubuntu but something I have done/installed may have messed it up. I can still get access to the hard drive/camera etc using /media/
but I need to know how to solve these problems when recommending kubuntu to others (e.g. my father).
Thanks in advance,
jonny

---

### Post by Sutekh on 2006-04-23
Is Konqueror trying to automatically mount the USB hard drive when you plug it in?

Can you provide the output from this command, which will list the available partitions, and hopefully the USB hard drive```
sudo fdisk -l
```

What are the contents of your fstab (mounting configuration file)? This command will print them to screen
```
cat /etc/fstab
```

---

### Post by jonnymccullagh on 2006-04-23
When I plug the hard drive (or a memory card) in knonqueror tries to show the contents using an address like above but then just shows the error about. The results of fdisk show the USB drive as sde1:
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       15334   123170323+   7  HPFS/NTFS
/dev/hda2   *       15335       19285    31736407+  83  Linux
/dev/hda3           19286       19457     1381590    5  Extended
/dev/hda5           19286       19457     1381558+  82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        9964    80027797+   f  W95 Ext'd (LBA)
/dev/hdb5               2        9964    80027766    b  W95 FAT32

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        9729    78148161    c  W95 FAT32 

The fstab is below (i have a few FAT, NTFS mounts):


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb5       /media/shared  vfat    iocharset=utf8,umask=000   0       0
/dev/hda1       /home/jonny/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb5       /home/jonny/shared  vfat    iocharset=utf8,umask=000   0       0

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0

---

