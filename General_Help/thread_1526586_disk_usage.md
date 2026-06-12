---
title: "disk usage"
date: 2010-07-08
forum: General Help
---

### Post by kaushalshriyan on 2010-07-08
Hi,

I have a weird issue about disk space on Ubuntu Hardy Server 8.04. I
do not get count of approximately 43Gb, I have rebooted the server
too. It did not worked too. Please suggest.

root at test:/# du -hs /* /.[^.]*
0	/backuplogdir
0	/backuplogdir_oct09
6.1M	/bin
36M	/boot
803G	/deliveryreports
36K	/dev
7.7M	/etc
2.7G	/home
0	/initrd
0	/initrd.img
0	/initrd.img.old
240M	/lib
0	/lib64
98G	/logfiles
0	/log-test
0	/media
0	/mnt
0	/opt
du: cannot access `/proc/21175/task/21175/fd/4': No such file or directory
du: cannot access `/proc/21175/task/21175/fdinfo/4': No such file or directory
du: cannot access `/proc/21175/fd/4': No such file or directory
du: cannot access `/proc/21175/fdinfo/4': No such file or directory
0	/proc
0	/REC-test
68K	/root
7.8M	/sbin
0	/srv
0	/sys
732G	/tmp
5.6G	/usr
460M	/var
0	/vmlinuz
0	/vmlinuz.old
du: cannot access `/.[^.]*': No such file or directory
root at test:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              70G   51G   19G  74% /
varrun                3.6G   64K  3.6G   1% /var/run
varlock               3.6G     0  3.6G   0% /var/lock
udev                  3.6G   32K  3.6G   1% /dev
devshm                3.6G     0  3.6G   0% /dev/shm
/dev/sda5             464M   46M  394M  11% /boot
ent-nfs:/mnt/data3/RECEIPTS
                      1.1T  1.1T   52G  96% /deliveryreports/RECEIPTS
ent-nfs:/mnt/data2/logfiles
                      1.1T   99G 1020G   9% /logfiles
core-logging:/tmp/backuplogdir
                      927G  844G   84G  92% /tmp/backuplogdir
root at test:/#

Thanks,

Kaushal

---

