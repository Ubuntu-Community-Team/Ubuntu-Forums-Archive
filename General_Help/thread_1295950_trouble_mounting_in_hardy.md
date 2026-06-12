---
title: "trouble mounting in hardy"
date: 2009-10-20
forum: General Help
---

### Post by unitedwefall on 2009-10-20
Hey

I did a clean install of 8.04 because i was getting quite a few bugs with 9.04 on everything seems to be going fine, except im having trouble mounting my external harf disk. I installed from a USB drive, and the probel with mounting from your USB ports seems to be a common one after an install like this. So i dutifully searched and found quite a few fixes, but none of them seem to be working for me. It seems people with problems are posting the results of

```
 sudo fdisk -l
```

which for me is

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          15      120456   de  Dell Utility
/dev/sda2              16        1321    10485760    7  HPFS/NTFS
/dev/sda3   *        1321       19015   142124720    7  HPFS/NTFS
/dev/sda4           19016       38914   159831838    f  W95 Ext'd (LBA)
/dev/sda5           38587       38914     2620416   dd  Unknown
/dev/sda6           37788       38586     6417936   82  Linux swap / Solaris
/dev/sda7           19016       37020   144625131   83  Linux
/dev/sda8           37021       37787     6160896   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200048565760 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45b045af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS

```

(it is the 200GB disk at the bottom there)

and my fstab looks like this 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda7
UUID=f7da1f61-7677-431b-b130-dac6c0057522  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda8
UUID=c6bbeac2-b12a-4d3b-8e7b-6f724bbbb56c  none           swap         sw                          0  0  

/dev/scd0                                  /media/cdrom1  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/scd1                                  /media/cdrom2  udf,iso9660  user,noauto,exec,utf8       0  0  

```

I did make some changes to it but nothing seemed to work.

Please help if you have time!

---

### Post by uncle-c on 2009-10-20
It is quite straightforward; just entails some minor editing of your **/etc/fstab** file and the creation of a suitable mount point from where you can access the files which are housed on the USB drive

[http://ubuntuforums.org/showthread.php?t=767879](http://ubuntuforums.org/showthread.php?t=767879)

Just a quick reminder the above solution is for automatic mounting. If you want to mount when you please (and not at startup)  then you will have no make sure that the **/etc/fstab** file contains the **noauto** directive.

---

