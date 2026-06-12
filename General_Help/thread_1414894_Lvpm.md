---
title: "Lvpm"
date: 2010-02-24
forum: General Help
---

### Post by luisridaocruz on 2010-02-24
Hi,

I have used LVPM to resize my ubuntu root.disk from 25 GB to 30 GB.
But this was a big mistake because I had 61 GB in my /host drive and I seemed
to used it up all. I have not lost data because my work was in another partition
but Windows won't start up. I copy-paste the files ystem space usage (from ubuntu):

luisridaocruz@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             25G   22G  1.2G  95% /
udev                 1001M  332K 1000M   1% /dev
none                 1001M  252K 1001M   1% /dev/shm
none                 1001M   92K 1001M   1% /var/run
none                 1001M     0 1001M   0% /var/lock
none                 1001M     0 1001M   0% /lib/init/rw
/dev/sda1              61G   61G     0 100% /host
/dev/sdb1             233G  207G   27G  89% /media/New Volume
/dev/sda2              89G   52G   38G  59% /media/Data

How can I free up some of the memory in /host so that Windows will work?

Thanks in advance

---

