---
title: "incorrect disk usage/lost disk space?"
date: 2009-07-13
forum: General Help
---

### Post by iamnobody on 2009-07-13
it seems like i've lost a few gigs of hard drive space.  i installed ubuntu 9.04 today, overwriting my previous 8.04 installation.  my disk usage screenshot is attached.  my filesystem is on the /dev/sda5 partition and it is not used for data storage, so it really shouldn't take up too much space. disk usage analyzer says that my filesystem is 4.7G.  however, it also says 11.9G is used for this partition.  df -h also returns the seemingly incorrect value of memory used.  even when i run partimage to image this partition, it says that i have used 11.9G.  i've run fsck but it didn't change anything.  any ideas on what's wrong/how to fix it?  thanks.

results of df -h:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              20G   12G  6.9G  64% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  100K 1006M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  180K 1006M   1% /dev
tmpfs                1007M   76K 1006M   1% /dev/shm
lrm                  1007M  2.2M 1004M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda6              82G   75G  7.1G  92% /media/data

---

