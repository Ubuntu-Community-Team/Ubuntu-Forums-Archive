---
title: "Unable to delete read-only files"
date: 2010-08-21
forum: General Help
---

### Post by glendavee on 2010-08-21
I'm trying to delete files on a USB disk. If I try using terminal using rm, because files are write only. I can't change this, even as root using chmod or unmount mount. When I use fdisk I still can't reformat, either as superuser or root. I get the following :

Disk /dev/sdh: 16.1 GB, 16064184320 bytes
7 heads, 37 sectors/track, 121140 cylinders
Units = cylinders of 259 * 512 = 132608 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007cee2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *          32      121141    15683584    b  W95 FAT32
david@david-desktop:~$ sudo fdisk sdh1

Unable to open sdh1
david@david-desktop:~$ su 
Password: 
root@david-desktop:/home/david# fdisk sdh1

Unable to open sdh1
root@david-desktop:/home/david# 

Any suggestions?

---

### Post by Primefalcon on 2010-08-21
try opening it gparted, unmount it and format it (fat32 or fat16 are the most compatible) then try again

---

### Post by glendavee on 2010-08-21
Tried that. Reformating failed, with following error message

Error fsynching/closing /dev/sdh Input/Output error

---

### Post by AlphaLexman on 2010-08-21
What is the output of
```
mount
```
specifically the line with /dev/sdh1

And post the the output of
```
ls -l
```
of the files you want to delete.

---

### Post by glendavee on 2010-08-21
mount  : Here's the line with /dev/sdh1

/dev/sdh1 on /media/Transcend type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

output of ls -l
david@david-desktop:/media/Transcend$ ls -l
total 1536
drwx------ 3 david david    8192 2009-07-12 10:35 home
drwx------ 2 david david    8192 2010-05-06 10:30 install
-r-xr-xr-x 1 david david   14607 2010-05-06 10:27 ldlinux.sys
-rwxr-xr-x 1 david david    4530 2010-05-06 10:27 md5sum.txt
drwx------ 2 david david    8192 2010-05-06 10:30 pics
drwx------ 4 david david    8192 2010-05-06 10:30 pool
drwx------ 2 david david    8192 2010-05-06 10:30 preseed
drwx------ 3 david david   16384 2010-08-21 11:50 rdiff-backup-data
-rwxr-xr-x 1 david david     225 2010-05-06 10:27 README.diskdefines
drwx------ 2 david david    8192 2010-05-06 10:30 syslinux
-rwxr-xr-x 1 david david 1469477 2010-05-06 10:27 wubi.exe

---

### Post by AlphaLexman on 2010-08-21
> **glendavee said:**
> /dev/sdh1 on /media/Transcend type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
I am not familiar with the 'uhelper=udisks' or the 'shortname=mixed' parameters in your [ /etc/fstab ], but honestly, everything else looks as it should.

---

### Post by Primefalcon on 2010-08-21
you could try the following (make sure it is unmounted first)

```
dd if=/dev/urandom of=/dev/sdh bs=1M
```

then try recreating the partition and formatting it...

---

### Post by kukker32 on 2010-08-21
try delete it as root user..

enter terminal, and enter ```
gksudo nautilus
```if still not able to delete gain control over the files as your main user.. right click -> permissins or something like that...

now apply these settings and close the windows..
now as normal user try delete it again

---

### Post by glendavee on 2010-08-21
Tried Primefalcon's suggestion - no luck. When I execute the command nothing happens - blinking cursor, no message, even when left for 30 mins.
I'd already tried deleting as root, both in terminal and via gksudo nautilus
????

---

### Post by Primefalcon on 2010-08-21
> **glendavee said:**
> Tried Primefalcon's suggestion - no luck. When I execute the command nothing happens - blinking cursor, no message, even when left for 30 mins.
I'd already tried deleting as root, both in terminal and via gksudo nautilus
????
what I told you to do can take hours, the blinkin cursor means it's still working... when completed it'll return to a prompt

---

### Post by stoneage on 2010-08-21
A failing device will often show the same symptoms. Can you add and remove other data?

---

### Post by glendavee on 2010-08-22
I can't copy files to the disk - message "destination is read only"

---

### Post by glendavee on 2010-08-22
More info
I tried a file check using gparted. Didn't work. Error message is 
\RDIFF ~1\BACKUP.LOG is 117052k but it has 4363 clusters (34904k)

This means nothing to me!!

---

