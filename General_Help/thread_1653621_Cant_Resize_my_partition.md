---
title: "Cant Resize my partition"
date: 2010-12-27
forum: General Help
---

### Post by hisham_master on 2010-12-27
HI EVERYONE
I have problem with my partition I cant resize,do anything with it using Gparted or any other program 
I saved the details of Gparted report when I wanted to check the partition

GParted 0.6.2

Libparted 2.3
Check and repair file system (ntfs) on /dev/sda1  00:00:10    ( ERROR )
         
calibrate /dev/sda1  00:00:00    ( SUCCESS )
         
path: /dev/sda1
start: 63
end: 128021984
size: 128021922 (61.05 GiB)
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:10    ( ERROR )
         
ntfsresize -P -i -f -v /dev/sda1
         
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 65547219456 bytes (65548 MB)
Current device size: 65547224064 bytes (65548 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Cluster 1167846 is referenced multiple times!
Cluster 1167847 is referenced multiple times!
ERROR: Filesystem check failed!
ERROR: 2 clusters are referenced multiply times.
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

=======================================

---

### Post by mikewhatever on 2010-12-27
> NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE! The usage of the /f parameter is very IMPORTANT! No modification was and will be made to NTFS by this software until it gets repaired.

It's asking you to fix the filesystem errors by booting Windows and running chdsk /f .... Have you done that?

---

