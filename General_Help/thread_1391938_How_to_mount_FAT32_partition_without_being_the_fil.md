---
title: "How to mount FAT32 partition without being the files owned by root"
date: 2010-01-27
forum: General Help
---

### Post by oier on 2010-01-27
Hi,
I want to mount my FAT32 partition automatically on startup. It gets mounted but the problem is that all the files in the FAT32 partition are shown as owned by root. Because of that I can't  paste files or write to this partition.
Do you know how I can avoid this? This is my fstab file
```

# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=e2188bd8-e0cb-4e56-a868-560e556620a7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0585a541-d1d5-4732-95da-8a9a1e9cd5bc none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sda1
UUID=4268-37EC /home/TheFAT32Partition vfat iocharset=utf8,umask=000 0 3

```
I have tried changing UUID to dev/sda1, puting defaults etc, nothing helps. Has it got something to do with umask maybe?
Thanks,

---

### Post by Leppie on 2010-01-27
comment out the entry in fstab, then add yourself to the fuse group:
```
sudo useradd <username> fuse
```

---

### Post by bodhi.zazen on 2010-01-27
If you use fstab you need to specify ownership.

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Morbius1 on 2010-01-27
> UUID=4268-37EC /home/TheFAT32Partition vfat iocharset=utf8,umask=000 0 [COLOR=Blue]3[/COLOR]Except for the last digit ( it should be either a 0,1, or 2 ), and the fact that the mount point is in an unusual location ( off /home instead of off /home/username ) I don't see anything wrong with this. 

It's true that it would be owned by root but your umask gives read write permissions to everybody.

You might want to output the following command just to verify that the uuid and filesystem type are correct:

**sudo blkid -c /dev/null**

---

### Post by oier on 2010-01-27
Many thanks, it works! the trick was to add the uid option. This how it worked for me:
```

#/dev/sda1 
UUID=4268-37EC /home/username/myfat32partition/ vfat uid=username iocharset=utf8, umask=000 0 0

```Thanks to everybody again!

---

