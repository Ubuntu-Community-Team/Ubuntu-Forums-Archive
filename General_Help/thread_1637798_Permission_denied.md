---
title: "Permission denied"
date: 2010-12-04
forum: General Help
---

### Post by NCLI on 2010-12-04
I really don't understand this. I can't access big parts of my /RAID partition without being root, what is wrong here??

I've run both "chmod -R 666 /RAID" and "chown -R me:me /RAID", and I can see that the permissions are correct when I run ls -l as root, so why can't I access them??

"ls -l /RAID" :
```
drw-rw-rw- 40 me me 4096 2010-12-05 04:00 Backup
drw-rw-rw-  2 me me 4096 2010-12-03 09:46 lost+found
drw-rw-rw- 17 me me 4096 2010-12-05 00:48 Media

```

"ls -l /" :
```
drwxr-xr-x   2 root root  4096 2010-12-01 23:40 bin
drwxr-xr-x   3 root root  4096 2010-12-02 06:33 boot
drwxr-xr-x  16 root root  3920 2010-12-03 19:22 dev
drwxr-xr-x 130 root root 12288 2010-12-05 03:24 etc
drwxr-xr-x   6 root root  4096 2010-10-09 00:20 home
lrwxrwxrwx   1 root root    32 2010-12-02 06:33 initrd.img -> boot/initrd.img-2.6.32-26-server
lrwxrwxrwx   1 root root    32 2010-09-28 06:38 initrd.img.old -> boot/initrd.img-2.6.32-25-server
drwxr-xr-x  16 root root 12288 2010-12-01 23:41 lib
drwxr-xr-x   7 root root 12288 2010-10-23 06:31 lib32
lrwxrwxrwx   1 root root     4 2010-05-22 13:29 lib64 -> /lib
drwx------   2 root root 16384 2010-05-22 01:25 lost+found
drwxr-xr-x   3 root root  4096 2010-05-22 02:15 media
drwxr-xr-x   3 root root  4096 2010-06-10 18:20 mnt
drwxr-xr-x   2 root root  4096 2010-05-22 01:27 opt
dr-xr-xr-x 230 root root     0 2010-12-03 19:22 proc
drw-rw-rw-   7 me   me    4096 2010-11-29 01:36 RAID
drwx------  15 root root  4096 2010-11-29 01:32 root
drwxr-xr-x   2 root root 12288 2010-12-01 23:43 sbin
drwxr-xr-x   2 root root  4096 2009-12-05 23:25 selinux
drwxr-xr-x   2 root root  4096 2010-05-22 01:27 srv
drwxr-xr-x  13 root root     0 2010-12-03 19:22 sys
drwxrwxrwt   9 root root  4096 2010-12-05 03:27 tmp
drwxr-xr-x  11 root root  4096 2010-05-22 14:05 usr
drwxr-xr-x  16 root root  4096 2010-11-25 00:47 var
lrwxrwxrwx   1 root root    29 2010-12-02 06:33 vmlinuz -> boot/vmlinuz-2.6.32-26-server
lrwxrwxrwx   1 root root    29 2010-09-28 06:38 vmlinuz.old -> boot/vmlinuz-2.6.32-25-server

```

---

### Post by conradin on 2010-12-04
is this software or hardware RAID? Also, what type of RAID?

---

### Post by NCLI on 2010-12-04
> **conradin said:**
> is this software or hardware RAID? Also, what type of RAID?
Software RAID5 using mdadm, with the ext4 filesystem.

mdadm --detail /dev/md0 :
> mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Wed Apr 14 18:02:11 2010
     Raid Level : raid5
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Dec  5 02:40:04 2010
          State : active, resyncing
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 76% complete

           UUID : ecfc3d80:e07faf1b:753e8d7c:6216f365 (local to host NCLI-SERVER)
         Events : 0.1002333

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       17        1      active sync   /dev/sdb1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1



---

### Post by asmoore82 on 2010-12-04
You should never, ever `chomd -R` with any numeric codes.

I know a lot of folks do it but it's still no good.

Your problem is that directories must have executable permissions to act "normal"

This should fix it: ```
chmod -R +rwX /RAID
```
^that "X" must be uppercase, it means add execute permission for directories
or keep execute permissions for files that already have it.

`chmod -R` is only meant for use with the relative letter codes, good examples are:
```
chmod -R o-rwx ... #remove all other users permissions
chmod -R o-w ... #revoke other users write permission
chmod -R g=u ... #copy user permissions to group
chmod -R ug+rwX ... #allow all for user/group **NOTE UPPERCASE X**
```

---

### Post by efflandt on 2010-12-04
Note that x permission has a different meaning for directories than for files.  The correct permission for most directories that have write permission for owner and can be accessed by others is 755.  Note that your RAID is drw-rw-rw-, while other directories are drwxr-xr-x.

So it is probably that you set incorrect directory permission (no x for access).  And it looks like you made that mistake recursively (for directories within that directory).

---

### Post by NCLI on 2010-12-04
> **asmoore82 said:**
> You should never, ever `chomd -R` with any numeric codes.

I know a lot of folks do it but it's still no good.

Your problem is that directories must have executable permissions to act "normal"

This should fix it: ```
chmod -R +rwX /RAID
```
^that "X" must be uppercase, it means add execute permission for directories
or keep execute permissions for files that already have it.

`chmod -R` is only meant for use with the relative letter codes, good examples are:
```
chmod -R o-rwx ... #remove all other users permissions
chmod -R o-w ... #revoke other users write permission
chmod -R g=u ... #copy user permissions to group
chmod -R ug+rwX ... #allow all for user/group **NOTE UPPERCASE X**
```
I wish they'd disable that functionality then -_-
> **efflandt said:**
> Note that x permission has a different meaning for directories than for files.  The correct permission for most directories that have write permission for owner and can be accessed by others is 755.  Note that your RAID is drw-rw-rw-, while other directories are drwxr-xr-x.

So it is probably that you set incorrect directory permission (no x for access).  And it looks like you made that mistake recursively (for directories within that directory).
Thanks a lot guys, I didn't know this. Solves quite a few problems I've been having. :oops:

---

