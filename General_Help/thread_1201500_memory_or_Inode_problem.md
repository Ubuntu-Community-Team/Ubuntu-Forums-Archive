---
title: "memory or Inode problem?"
date: 2009-07-01
forum: General Help
---

### Post by rekblom on 2009-07-01
My xubuntu server has started behaving badly. I suspect that the problem has to do with available memory on the root, when checking I get:

bioinf@dyn0921:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3             261G  7.8G  245G   4% /
varrun                4.0G  132K  4.0G   1% /var/run
varlock               4.0G     0  4.0G   0% /var/lock
udev                  4.0G   60K  4.0G   1% /dev
devshm                4.0G     0  4.0G   0% /dev/shm
/dev/sdb1             183M  156M   17M  91% /boot
/dev/sdb2             187G   15G  163G   9% /data
/dev/sda2             466G  212G  255G  46% /media/win

bioinf@dyn0921:~$ df -ih
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sdb3               261K    261K       0  100% /
varrun                 1000K      65   1000K    1% /var/run
varlock                1000K       2   1000K    1% /var/lock
udev                   1000K    3.0K    997K    1% /dev
devshm                 1000K       1   1000K    1% /dev/shm
/dev/sdb1                48K      78     47K    1% /boot
/dev/sdb2               187K     418    186K    1% /data
/dev/sda2               259M    4.0M    255M    2% /media/win

What can I do about this?
/Robert

---

