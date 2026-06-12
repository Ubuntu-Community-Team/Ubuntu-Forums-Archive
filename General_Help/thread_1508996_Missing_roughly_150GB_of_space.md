---
title: "Missing roughly 150GB of space"
date: 2010-06-13
forum: General Help
---

### Post by xlr8ed on 2010-06-13
Ran in to a bit of an issue. I have two 500G drives set to RAID0 within that I have a single directory (Storage00) in root that has a about 600G with of data. That one directory is rsync'ed to two different USB drives(Storage01 & Storage02) nightly. The two USB drives are showing up correctly as is the directory itself (Storage00). However root is showing almost full and I can't locate the missing "space".

```
root@Grover:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/pdc_fbjhaicf3
                      826G  719G   65G  92% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  752K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  156K  1.8G   1% /dev
tmpfs                 1.8G     0  1.8G   0% /dev/shm
lrm                   1.8G  2.2M  1.8G   1% /lib/modules/2.6.28-18-server/volatile
/dev/mapper/pdc_fbjhaicf1
                       92M   44M   44M  50% /boot
/dev/mapper/pdc_fbjhaicf4
                       83G  222M   79G   1% /home
/dev/sdc1             925G  571G  308G  66% /storage01
/dev/sdd1             925G  571G  308G  66% /storage02

```

```
root@Grover:/# df -Th | grep -v "fs" | sort
/dev/mapper/pdc_fbjhaicf1
/dev/mapper/pdc_fbjhaicf3
/dev/mapper/pdc_fbjhaicf4
/dev/sdc1     ext3    925G  571G  308G  66% /storage01
/dev/sdd1     ext3    925G  571G  308G  66% /storage02
              ext3    826G  719G   65G  92% /
              ext3     83G  222M   79G   1% /home
              ext3     92M   44M   44M  50% /boot
Filesystem    Type    Size  Used Avail Use% Mounted on

```

```
root@Grover:/# sudo du -h --max-depth=1 / | sort
du: cannot access `/proc/5032/task/5032/fd/3': No such file or directory
du: cannot access `/proc/5032/task/5032/fdinfo/3': No such file or directory
du: cannot access `/proc/5032/fd/3': No such file or directory
du: cannot access `/proc/5032/fdinfo/3': No such file or directory
0       /proc
0       /sys
12K     /tmp
156K    /dev
16K     /lost+found
1.7T    /
300M    /lib
314M    /var
38M     /boot
38M     /home
4.0K    /mnt
4.0K    /opt
4.0K    /selinux
4.0K    /srv
493M    /usr
5.3M    /etc
571G    /storage01
571G    /storage02
586G    /storage00
6.1M    /bin
6.8M    /sbin
8.0K    /media
84K     /root

```

---

### Post by xlr8ed on 2010-06-14
For some reason some files were moved to the mount point, and then the USB drive was remounted over it. Unsure how all that happened, but I solved my own issue.

---

