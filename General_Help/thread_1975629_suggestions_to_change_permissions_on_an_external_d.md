---
title: "suggestions to change permissions on an external drive from MAC hfsplus"
date: 2012-05-07
forum: General Help
---

### Post by linux_tech on 2012-05-07
Trying to copy files from mac drive.  Can see folders but permissions errors when trying to copyfiles. 
mount returns:/dev/sdc2 on /media/Macintosh HD type hfsplus (ro,nosuid,nodev,uhelper=udisks) 

Do not have a mac computer to access dive from.  Only have a ubuntu pcto work from . Drive is mounted ro. How to either take ownership, change permissions, etc to be able to copy the files.  Side note- some of the folders on Macintosh HD I was able to copy but one that I really need to access, I can see the subfolders in folder but permission denied when trying to copy.  Any suggestions welcome. Thanks. If all else fails I will run testdisk on the drive to recover the files. I have tried using chmod to change the permissions, also  gksudo nautilus.   I have to go out for a bit I'll check back in a little while and try any suggestions

---

### Post by hal8000 on 2012-05-07
You can't write to hfsplus partitions from linux, but should be able to read from them and copy onto your linux partition. Once on your linux partition you can change partitions.


This is what mount returns on my hfsplus partition:

/dev/sdb3 on /root/tmp type hfsplus (ro)


I mounted my system under /root/tmp and posted permissions for
comparison:

[root@orac tmp]# ls -l
total 15476
drwxrwxr-x 1 root cdwriter       30 Sep 24  2011 Applications/
drwxr-xr-x 1 root root           39 Aug 30  2011 bin/
-rw-r--r-- 1 root games      263808 Oct 12  2011 boot
drwxrwxr-t 1 root cdwriter        2 Jun 18  2011 cores/
dr-xr-xr-x 1 root root            2 Jun 18  2011 dev/
lrwxr-xr-x 1 root root           11 Oct 12  2011 etc -> private/etc/
drwxr-xr-x 1 root root            6 Oct 12  2011 Extra/
dr-xr-xr-x 1 root games           2 Oct 12  2011 home/
drwxr-xr-x 1 root root           60 Oct 12  2011 Library/
-rw-r--r-- 1 root root     15565140 Jul 27  2011 mach_kernel
dr-xr-xr-x 1 root games           2 Oct 12  2011 net/
drwxr-xr-x 1 root root            2 Jun 18  2011 Network/
drwxr-xr-x 1 root root            6 Oct 12  2011 private/
drwxr-xr-x 1 root root           62 Oct 12  2011 sbin/
drwxr-xr-x 1 root root            4 Aug 30  2011 System/
lrwxr-xr-x 1 root root           11 Oct 12  2011 tmp -> private/tmp/
drwxr-xr-x 1 root cdwriter        4 Aug 30  2011 Users/
drwxr-xr-x 1 root root           10 Oct 12  2011 usr/
lrwxr-xr-x 1 root root           11 Oct 12  2011 var -> private/var/
drwxrwxrwt 1 root cdwriter        5 Apr  7 16:41 Volumes/


At this stage I will point out that my Mac Install was the hacktint0sh
project, so possibly not the same as your install, but the hfsplus filesystem will be the same. 

Which directories do you get permission denied?

---

### Post by linux_tech on 2012-05-07
Thanks for the reply. I was trying to copy a music directory containing subfolders. There may be some other issues along with the permissions.  the drive disappears sometimes in nautilus. Tried to cp from term but
get different error.  Beginning to think the drive may have a some bad sectors.  Going to try recovery on drive and see how that works out

---

