---
title: "Disk Usage Analyzer missing 40Gb"
date: 2010-05-26
forum: General Help
---

### Post by ianhaycox on 2010-05-26
I'm a bit stumped by a bunch of 'missing' disk space.

My root (/) partition filled up and I recovered by moving a bunch of errant MythTV recordings, but it's still showing 47Gb used whereas the following output only shows < 9Gb used.

Any ideas ?

```

$ sudo du -xhs /
[sudo] password for ian: 
8.7G	/

```

```

$ sudo baobab

```

showed / as 8.6Gb but the filesystem as 64.2GB capacity and used 46.5Gb  (see screenshot)  BTW - I unchecked all the file systems except / in preferences.

and

```

$ sudo find / -mount -size +50M -print
/var/lib/mysql/mythconverg/recordedseek.MYD
/var/lib/mysql/mythconverg/recordedseek.MYI
$ 

```

finally,

```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              65G   47G   15G  77% /
udev                  1.5G  372K  1.5G   1% /dev
none                  1.5G  1.5M  1.5G   1% /dev/shm
none                  1.5G  336K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sdb1             917G  724G  147G  84% /home
/dev/sdc1              39G   25G   13G  68% /VirtualBox
/dev/sdc3             148G  1.8G  138G   2% /MythTv
/dev/sda3             845G  673G  129G  84% /backups

```

Thanks

---

### Post by dino99 on 2010-05-26
force a fsck on next boot:

sudo shutdown -F -r now

you can make room by installing and using: localepurge, deborphan, gconf-cleaner, bleachbit

if you want to check your devices and partitions, boot with partedmagic [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by ianhaycox on 2010-05-26
Hi,

Thanks for that, but it actually much simpler. Typically after posting I realised that at some time /backups (populated via cron/rsync) was used whilst not mounted !!!

so fixed via,

```

$ sudo umount /backups
$ cd /backups
$ sudo rm -rf --one-file-system *
$ sudo $ mount -a
$ df -h
$ sudo mount -a
ian@ianh:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              65G  8.9G   53G  15% /
udev                  1.5G  372K  1.5G   1% /dev
none                  1.5G  1.5M  1.5G   1% /dev/shm
none                  1.5G  336K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sdb1             917G  724G  147G  84% /home
/dev/sdc1              39G   25G   13G  68% /VirtualBox
/dev/sdc3             148G  1.8G  138G   2% /MythTv
/dev/sda3             845G  673G  129G  84% /backups

```

et voila. Too quick to blame something else other than user error. Doh.

---

### Post by dino99 on 2010-05-26
sudo apt-get --remove chouchen  :P

---

