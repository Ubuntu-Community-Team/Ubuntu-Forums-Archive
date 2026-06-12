---
title: "free space disapeared"
date: 2012-05-21
forum: General Help
---

### Post by amir1981 on 2012-05-21
Hi, I encountered with this weird thing:
I had more than 2 Gig of free space on my ubuntu (installed under virtual box) 
but when I was working it suddenly start shrinking and get into 0. I restart the computer and it was still  almost zero  so I delete some files to get some space now I have  around 4 gigs but    Disk usage analyzer tells me that I have 9.5 gig free  while  df  shows this:
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              24G   18G  4.5G  81% /
none                  1.2G  272K  1.2G   1% /dev
none                  1.2G  208K  1.2G   1% /dev/shm
none                  1.2G  284K  1.2G   1% /var/run
none                  1.2G     0  1.2G   0% /var/lock
none                  1.2G     0  1.2G   0% /lib/init/rw
/dev/sdb1             7.9G  4.0G  3.5G  54% /mnt/sdb1
/dev/sr0               39M   39M     0 100% /media/VBOXADDITIONS_4.0.8_71778

and  it seems I just have access to 4.4 Gig!  So  what happened to my other space? Is there any way to recover it?

thanks

---

### Post by roelforg on 2012-05-21
Did the disk analyzer show in GB or GiB (there's a difference in the units, it might be what causes the (appearant) loss of space)?

---

### Post by amir1981 on 2012-05-21
> **roelforg said:**
> Did the disk analyzer show in GB or GiB (there's a difference in the units, it might be what causes the (appearant) loss of space)?
GB 
I am almost sure that the space lost. It disappeared in front of my eyes.

---

### Post by tumutanzi.com on 2012-05-21
Are you sure you have allocated all the free space for your new file system?

---

### Post by lukeiamyourfather on 2012-05-21
To see where the space is being used try Baobab which should be installed by default.

---

### Post by amir1981 on 2012-05-21
> **tumutanzi.com said:**
> Are you sure you have allocated all the free space for your new file system?

Well, when I installed the Ubuntu yes but now I don't know I mean it seems something has happened that cause some part of the disk get unallocated, is it possible?

---

### Post by roelforg on 2012-05-21
> **amir1981 said:**
> Well, when I installed the Ubuntu yes but now I don't know I mean it seems something has happened that cause some part of the disk get unallocated, is it possible?

Did you factor in the swap space?
IIRC, the desktop installer lets you select a certain amount of space for ubuntu and it allocates a certain percentage to swap.
I think gparted can help you see what's swap and what's unallocated.

---

### Post by amir1981 on 2012-05-21
My disk size is around 30 GB  but as you  see  from the above post it has been divided into several sections 
/dev/sda1 24G 18G 4.5G 81% /
none 1.2G 272K 1.2G 1% /dev
none 1.2G 208K 1.2G 1% /dev/shm
none 1.2G 284K 1.2G 1% /var/run
none 1.2G 0 1.2G 0% /var/lock
none 1.2G 0 1.2G 0% /lib/init/rw

(sdb2  is another  partition that I add later)

what are all those  "none"  partitions?

---

### Post by roelforg on 2012-05-21
> **amir1981 said:**
> My disk size is around 30 GB  but as you  see  from the above post it has been divided into several sections 
/dev/sda1 24G 18G 4.5G 81% /
none 1.2G 272K 1.2G 1% /dev
none 1.2G 208K 1.2G 1% /dev/shm
none 1.2G 284K 1.2G 1% /var/run
none 1.2G 0 1.2G 0% /var/lock
none 1.2G 0 1.2G 0% /lib/init/rw

(sdb2  is another  partition that I add later)

what are all those  "none"  partitions?

They're virtual filesystems exported by kernel (modules), they don't have a physical device/partition to match them so they show up as none (IIRC fuse filesystems show up as none as well, but then again, they're exported by the fuse kernel module).
But that list doesn't show swap.
You could try gparted and see how large the linux extended/swap partitions are, because i suspect swap's taking the "missing" space on the hd.

---

### Post by amir1981 on 2012-05-21
Gparted shows:
 /dev/sda1   ext4  /  23.92 GiB  5.64 GiB  boot
/dev/sda2  extended   1.08 GiB  ----  ----
/dev/sda5  linux-swap         1.08   GiB  --- ---

---

### Post by amir1981 on 2012-05-21
Another thing is  when I try to find files grater than 1 gig:
sudo find / -name '*'  -size +1G
[sudo] password for amir: 
find: `/proc/1972/task/1972/fd/5': No such file or directory
find: `/proc/1972/task/1972/fdinfo/5': No such file or directory
find: `/proc/1972/fd/5': No such file or directory
find: `/proc/1972/fdinfo/5': No such file or directory
find: `/home/amir/.gvfs': Permission denied

---

### Post by roelforg on 2012-05-21
> **amir1981 said:**
> Another thing is  when I try to find files grater than 1 gig:
sudo find / -name '*'  -size +1G
[sudo] password for amir: 
find: `/proc/1972/task/1972/fd/5': No such file or directory
find: `/proc/1972/task/1972/fdinfo/5': No such file or directory
find: `/proc/1972/fd/5': No such file or directory
find: `/proc/1972/fdinfo/5': No such file or directory
find: `/home/amir/.gvfs': Permission denied

/proc is one of those kernel filesystems, it has info on the status of PROCcesses and changes all the time, so when find probes the directory, a file might be there...
But when it scans it, the process corresponding to it might've ended and that causes procfs to delete it's nodes so find errors on those files but it'll keep going.
The permission denied error is because .gvfs is the directory used for automounting certain types of filesystems, it's owned by root because it would cause permission errors down the line if not.

---

### Post by David Andersson on 2012-05-21
> **amir1981 said:**
> Disk usage analyzer tells me that I have 9.5 gig free  while  df  shows this:
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              24G   18G  4.5G  81% /
none                  1.2G  272K  1.2G   1% /dev
none                  1.2G  208K  1.2G   1% /dev/shm
none                  1.2G  284K  1.2G   1% /var/run
none                  1.2G     0  1.2G   0% /var/lock
none                  1.2G     0  1.2G   0% /lib/init/rw
/dev/sdb1             7.9G  4.0G  3.5G  54% /mnt/sdb1
/dev/sr0               39M   39M     0 100% /media/VBOXADDITIONS_4.0.8_71778

and  it seems I just have access to 4.4 Gig!  So  what happened to my other space? Is there any way to recover it?


Disk Usage Analyzer can sum up space from multiple devices/filesystems. The sum of /, sdb1 and media is close to 9.5G. See Disk Usage Analyzer > Edit > Preferences what file systems it considers.

[QUOTE=roelforg]You could try gparted and see how large the linux extended/swap partitions are, because i suspect swap's taking the "missing" space on the hd. [/QUOTE]
Normal swap usage would not make space disappear right before your eyes, not for the the /, sdb1 or media filesystems. (Maybe the "none" filesystems are partly in swap and partly in RAM.)

---

### Post by amir1981 on 2012-05-21
> **David Andersson said:**
> Disk Usage Analyzer can sum up space from multiple devices/filesystems. The sum of /, sdb1 and media is close to 9.5G. See Disk Usage Analyzer > Edit > Preferences what file systems it considers.


Normal swap usage would not make space disappear right before your eyes, not for the the /, sdb1 or media filesystems. (Maybe the "none" filesystems are partly in swap and partly in RAM.)

You are right for just  sda1 it show   5.6 GB  free space.  I have 4.4 GB now.
When the space start disappearing I could  actually see the free space shrinking with just  hitting the  refresh button.  I don't know what cause it

---

### Post by JKyleOKC on 2012-05-21
Check the size of /var/log and the files it contains. One of the most common causes of space vanishing "for no reason" is some runaway process writing to the logs in a tight loop. If you post the output of "ls -la /var/log/*" we'll be able to tell if that's what happened, and how to regain the lost space...

---

### Post by amir1981 on 2012-05-21
> **JKyleOKC said:**
> Check the size of /var/log and the files it contains. One of the most common causes of space vanishing "for no reason" is some runaway process writing to the logs in a tight loop. If you post the output of "ls -la /var/log/*" we'll be able to tell if that's what happened, and how to regain the lost space...
amir-laptop_[1]: ls -la /var/log/*
-rw-r--r-- 1 root              root      0 2011-01-17 11:43 /var/log/aptitude
-rw-r--r-- 1 root              root   1040 2011-01-15 19:29 /var/log/aptitude.1.gz
-rw-r----- 1 syslog            adm   11886 2012-05-21 16:17 /var/log/auth.log
-rw-r----- 1 syslog            adm   11289 2012-05-20 11:21 /var/log/auth.log.1
-rw-r----- 1 syslog            adm     705 2012-05-16 11:17 /var/log/auth.log.2.gz
-rw-r----- 1 syslog            adm     848 2012-05-11 12:03 /var/log/auth.log.3.gz
-rw-r----- 1 syslog            adm    1980 2012-05-02 11:17 /var/log/auth.log.4.gz
-rw-r----- 1 root              adm      31 2010-08-16 05:34 /var/log/boot
-rw-r--r-- 1 root              root   1010 2012-05-21 13:56 /var/log/boot.log
-rw-r--r-- 1 root              root  41645 2010-08-16 05:35 /var/log/bootstrap.log
-rw-rw---- 1 root              utmp   1536 2012-05-21 13:59 /var/log/btmp
-rw-rw---- 1 root              utmp     57 2012-05-02 11:05 /var/log/btmp.1.gz
-rw-r----- 1 syslog            adm   83404 2012-05-21 14:05 /var/log/daemon.log
-rw-r----- 1 syslog            adm   29006 2012-05-20 11:27 /var/log/daemon.log.1
-rw-r----- 1 syslog            adm    3805 2012-05-16 11:11 /var/log/daemon.log.2.gz
-rw-r----- 1 syslog            adm    4244 2012-05-11 12:04 /var/log/daemon.log.3.gz
-rw-r----- 1 syslog            adm    6088 2012-05-02 11:11 /var/log/daemon.log.4.gz
-rw-r----- 1 syslog            adm   37722 2012-05-21 13:59 /var/log/debug
-rw-r----- 1 syslog            adm    7532 2012-05-20 11:21 /var/log/debug.1
-rw-r----- 1 syslog            adm    2380 2012-05-16 11:05 /var/log/debug.2.gz
-rw-r----- 1 syslog            adm    2533 2012-05-11 12:03 /var/log/debug.3.gz
-rw-r----- 1 syslog            adm    3070 2012-05-02 11:06 /var/log/debug.4.gz
-rw-r----- 1 root              adm   26011 2012-05-21 13:56 /var/log/dmesg
-rw-r----- 1 root              adm   25633 2012-05-21 13:53 /var/log/dmesg.0
-rw-r----- 1 root              adm    8874 2012-05-21 13:51 /var/log/dmesg.1.gz
-rw-r----- 1 root              adm    8962 2012-05-21 13:26 /var/log/dmesg.2.gz
-rw-r----- 1 root              adm    8893 2012-05-21 13:25 /var/log/dmesg.3.gz
-rw-r----- 1 root              adm    9355 2012-05-21 13:19 /var/log/dmesg.4.gz
-rw-r--r-- 1 root              root      0 2012-03-03 07:59 /var/log/dpkg.log
-rw-r--r-- 1 root              root   9985 2012-03-02 18:51 /var/log/dpkg.log.1
-rw-r--r-- 1 root              root   5076 2011-01-17 11:44 /var/log/dpkg.log.10.gz
-rw-r--r-- 1 root              root  90486 2010-10-17 00:18 /var/log/dpkg.log.11.gz
-rw-r--r-- 1 root              root    364 2012-01-26 10:39 /var/log/dpkg.log.2.gz
-rw-r--r-- 1 root              root    702 2012-01-23 16:17 /var/log/dpkg.log.3.gz
-rw-r--r-- 1 root              root   1044 2011-07-15 09:48 /var/log/dpkg.log.4.gz
-rw-r--r-- 1 root              root    836 2011-06-05 14:36 /var/log/dpkg.log.5.gz
-rw-r--r-- 1 root              root   1768 2011-05-19 15:42 /var/log/dpkg.log.6.gz
-rw-r--r-- 1 root              root   1646 2011-04-04 14:16 /var/log/dpkg.log.7.gz
-rw-r--r-- 1 root              root   5682 2011-02-02 00:03 /var/log/dpkg.log.8.gz
-rw-r--r-- 1 root              root   9796 2011-01-18 22:51 /var/log/dpkg.log.9.gz
-rw-r--r-- 1 root              root  24024 2010-10-08 01:37 /var/log/faillog
-rw-r--r-- 1 root              root   2391 2011-01-17 11:49 /var/log/fontconfig.log
-rw-r--r-- 1 root              root      0 2010-10-10 16:08 /var/log/jockey.log
-rw-r--r-- 1 root              root  20473 2010-10-10 16:08 /var/log/jockey.log.1
-rw-r----- 1 syslog            adm  250136 2012-05-21 13:59 /var/log/kern.log
-rw-r----- 1 syslog            adm   45762 2012-05-20 11:36 /var/log/kern.log.1
-rw-r----- 1 syslog            adm   19442 2012-05-16 11:05 /var/log/kern.log.2.gz
-rw-r----- 1 syslog            adm   20549 2012-05-11 12:03 /var/log/kern.log.3.gz
-rw-r----- 1 syslog            adm   29589 2012-05-02 11:06 /var/log/kern.log.4.gz
-rw-rw-r-- 1 root              utmp 292292 2012-05-21 13:54 /var/log/lastlog
-rw-r----- 1 syslog            adm       0 2011-02-04 23:13 /var/log/lpr.log
-rw-r----- 1 syslog            adm     140 2011-02-01 23:48 /var/log/lpr.log.1
-rw-r----- 1 syslog            adm       0 2010-10-08 01:06 /var/log/mail.err
-rw-r----- 1 syslog            adm       0 2010-10-08 01:06 /var/log/mail.info
-rw-r----- 1 syslog            adm       0 2010-10-08 01:06 /var/log/mail.log
-rw-r----- 1 syslog            adm       0 2010-10-08 01:06 /var/log/mail.warn
-rw-r----- 1 syslog            adm  220469 2012-05-21 14:01 /var/log/messages
-rw-r----- 1 syslog            adm   40058 2012-05-20 11:38 /var/log/messages.1
-rw-r----- 1 syslog            adm   17329 2012-05-16 11:18 /var/log/messages.2.gz
-rw-r----- 1 syslog            adm   18288 2012-05-11 12:07 /var/log/messages.3.gz
-rw-r----- 1 syslog            adm   26522 2012-05-02 12:04 /var/log/messages.4.gz
-rw-r--r-- 1 root              root   7581 2012-05-21 13:56 /var/log/pm-powersave.log
-rw-r--r-- 1 root              root   4758 2012-05-02 11:58 /var/log/pm-powersave.log.1
-rw-r--r-- 1 root              root    220 2012-04-04 11:34 /var/log/pm-powersave.log.2.gz
-rw-r--r-- 1 root              root    190 2012-02-27 09:36 /var/log/pm-powersave.log.3.gz
-rw-r--r-- 1 root              root    262 2012-01-25 10:43 /var/log/pm-powersave.log.4.gz
-rw-r--r-- 1 root              root      0 2012-01-19 07:38 /var/log/pm-suspend.log
-rw-r--r-- 1 root              root   3962 2012-01-17 23:38 /var/log/pm-suspend.log.1
-rw-r--r-- 1 root              root      0 2010-08-16 05:35 /var/log/pycentral.log
-rw-r----- 1 syslog            adm  165796 2012-05-21 16:17 /var/log/syslog
-rw-r----- 1 syslog            adm  177698 2012-05-21 13:34 /var/log/syslog.1
-rw-r----- 1 syslog            adm   14516 2012-05-20 11:36 /var/log/syslog.2.gz
-rw-r----- 1 syslog            adm    3319 2012-05-18 07:35 /var/log/syslog.3.gz
-rw-r----- 1 syslog            adm   26562 2012-05-16 11:17 /var/log/syslog.4.gz
-rw-r----- 1 syslog            adm   14083 2012-05-11 12:04 /var/log/syslog.5.gz
-rw-r----- 1 syslog            adm   14211 2012-05-04 11:17 /var/log/syslog.6.gz
-rw-r----- 1 syslog            adm    1179 2012-05-03 07:35 /var/log/syslog.7.gz
-rw-r--r-- 1 root              root 159867 2012-05-21 13:55 /var/log/udev
-rw-r----- 1 syslog            adm       0 2010-10-08 01:06 /var/log/ufw.log
-rw-r----- 1 syslog            adm    6604 2012-05-21 13:59 /var/log/user.log
-rw-r----- 1 syslog            adm    1054 2012-05-20 11:21 /var/log/user.log.1
-rw-r----- 1 syslog            adm     506 2012-05-16 11:05 /var/log/user.log.2.gz
-rw-r----- 1 syslog            adm     502 2012-05-11 12:03 /var/log/user.log.3.gz
-rw-r----- 1 syslog            adm     571 2012-05-02 11:05 /var/log/user.log.4.gz
-rw-r--r-- 1 root              root 151099 2010-10-17 00:36 /var/log/vboxadd-install.log
-rw-r--r-- 1 root              root     73 2010-10-17 00:36 /var/log/vboxadd-install-x11.log
-rw-r--r-- 1 root              root    103 2010-10-17 00:36 /var/log/VBoxGuestAdditions.log
-rw-r--r-- 1 root              root    126 2010-10-17 00:34 /var/log/VBoxGuestAdditions-uninstall.log
-rw-rw-r-- 1 root              utmp  52224 2012-05-21 15:49 /var/log/wtmp
-rw-rw-r-- 1 root              utmp   1284 2012-05-02 11:54 /var/log/wtmp.1.gz
-rw-r--r-- 1 root              root  25289 2012-05-21 13:56 /var/log/Xorg.0.log
-rw-r--r-- 1 root              root  25692 2012-05-21 13:51 /var/log/Xorg.0.log.old
-rw-r--r-- 1 root              root  25289 2012-01-17 15:14 /var/log/Xorg.1.log

/var/log/apache2:
total 224
drwxr-x---  2 root adm  4096 2012-05-20 11:38 .
drwxr-xr-x 15 root root 4096 2012-05-21 13:56 ..
-rw-r-----  1 root adm     0 2012-04-25 14:34 access.log
-rw-r-----  1 root adm   556 2012-04-24 17:34 access.log.1
-rw-r-----  1 root adm   204 2012-03-21 01:26 access.log.2.gz
-rw-r-----  1 root adm   219 2011-05-19 18:11 access.log.3.gz
-rw-r-----  1 root adm   201 2011-03-04 11:58 access.log.4.gz
-rw-r-----  1 root adm   483 2011-01-16 20:45 access.log.5.gz
-rw-r-----  1 root adm  1160 2012-05-21 13:56 error.log
-rw-r-----  1 root adm   445 2012-05-20 11:38 error.log.1
-rw-r-----  1 root adm   262 2012-03-12 14:58 error.log.10.gz
-rw-r-----  1 root adm   254 2012-03-04 07:51 error.log.11.gz
-rw-r-----  1 root adm   278 2012-02-27 10:12 error.log.12.gz
-rw-r-----  1 root adm   253 2012-02-05 07:48 error.log.13.gz
-rw-r-----  1 root adm   269 2012-01-29 07:58 error.log.14.gz
-rw-r-----  1 root adm   317 2012-01-22 07:47 error.log.15.gz
-rw-r-----  1 root adm   347 2012-01-15 09:58 error.log.16.gz
-rw-r-----  1 root adm   301 2012-01-08 07:59 error.log.17.gz
-rw-r-----  1 root adm   281 2012-01-02 10:55 error.log.18.gz
-rw-r-----  1 root adm   290 2011-12-18 08:00 error.log.19.gz
-rw-r-----  1 root adm   274 2011-12-11 12:18 error.log.20.gz
-rw-r-----  1 root adm   264 2011-12-05 11:26 error.log.21.gz
-rw-r-----  1 root adm   286 2011-11-27 13:04 error.log.22.gz
-rw-r-----  1 root adm   326 2011-11-20 17:54 error.log.23.gz
-rw-r-----  1 root adm   338 2011-11-13 07:47 error.log.24.gz
-rw-r-----  1 root adm   265 2011-11-06 21:12 error.log.25.gz
-rw-r-----  1 root adm   275 2011-10-12 12:48 error.log.26.gz
-rw-r-----  1 root adm   302 2011-09-29 10:59 error.log.27.gz
-rw-r-----  1 root adm   265 2011-09-05 18:14 error.log.28.gz
-rw-r-----  1 root adm   262 2011-08-16 21:38 error.log.29.gz
-rw-r-----  1 root adm   274 2012-05-16 11:18 error.log.2.gz
-rw-r-----  1 root adm   256 2011-08-04 08:02 error.log.30.gz
-rw-r-----  1 root adm   315 2011-07-24 16:36 error.log.31.gz
-rw-r-----  1 root adm   266 2011-07-17 07:41 error.log.32.gz
-rw-r-----  1 root adm   342 2011-07-10 00:39 error.log.33.gz
-rw-r-----  1 root adm   283 2011-07-03 08:03 error.log.34.gz
-rw-r-----  1 root adm   290 2011-06-26 15:38 error.log.35.gz
-rw-r-----  1 root adm   290 2011-06-19 21:29 error.log.36.gz
-rw-r-----  1 root adm   278 2011-06-12 14:06 error.log.37.gz
-rw-r-----  1 root adm   332 2011-06-05 14:50 error.log.38.gz
-rw-r-----  1 root adm   304 2011-05-29 14:51 error.log.39.gz
-rw-r-----  1 root adm   275 2012-05-11 12:07 error.log.3.gz
-rw-r-----  1 root adm   502 2011-05-22 07:49 error.log.40.gz
-rw-r-----  1 root adm   290 2011-05-19 12:36 error.log.41.gz
-rw-r-----  1 root adm   295 2011-04-01 12:35 error.log.42.gz
-rw-r-----  1 root adm   262 2011-03-22 12:13 error.log.43.gz
-rw-r-----  1 root adm   314 2011-03-17 21:08 error.log.44.gz
-rw-r-----  1 root adm   375 2011-03-06 07:46 error.log.45.gz
-rw-r-----  1 root adm   265 2011-03-01 18:12 error.log.46.gz
-rw-r-----  1 root adm   287 2011-02-13 22:03 error.log.47.gz
-rw-r-----  1 root adm   966 2011-02-01 22:50 error.log.48.gz
-rw-r-----  1 root adm   366 2012-05-02 12:03 error.log.4.gz
-rw-r-----  1 root adm   274 2012-04-24 14:39 error.log.5.gz
-rw-r-----  1 root adm   261 2012-04-18 13:59 error.log.6.gz
-rw-r-----  1 root adm   265 2012-04-04 12:02 error.log.7.gz
-rw-r-----  1 root adm   351 2012-03-29 20:03 error.log.8.gz
-rw-r-----  1 root adm   276 2012-03-20 17:59 error.log.9.gz
-rw-r--r--  1 root root    0 2011-01-16 20:09 other_vhosts_access.log

/var/log/apparmor:
total 8
drwxr-xr-x  2 root root 4096 2010-03-30 15:59 .
drwxr-xr-x 15 root root 4096 2012-05-21 13:56 ..

/var/log/apt:
total 116
drwxr-xr-x  2 root root  4096 2012-03-03 07:59 .
drwxr-xr-x 15 root root  4096 2012-05-21 13:56 ..
-rw-r--r--  1 root root     0 2012-03-03 07:59 history.log
-rw-r--r--  1 root root  2169 2011-01-17 11:42 history.log.10.gz
-rw-r--r--  1 root root 13574 2010-10-16 23:53 history.log.11.gz
-rw-r--r--  1 root root   272 2012-03-02 18:51 history.log.1.gz
-rw-r--r--  1 root root   154 2012-01-26 10:39 history.log.2.gz
-rw-r--r--  1 root root   225 2012-01-23 16:17 history.log.3.gz
-rw-r--r--  1 root root   189 2011-07-15 09:48 history.log.4.gz
-rw-r--r--  1 root root   244 2011-06-05 14:36 history.log.5.gz
-rw-r--r--  1 root root   396 2011-05-19 15:42 history.log.6.gz
-rw-r--r--  1 root root   137 2011-04-04 14:16 history.log.7.gz
-rw-r--r--  1 root root   909 2011-02-02 00:03 history.log.8.gz
-rw-r--r--  1 root root   135 2011-01-18 22:51 history.log.9.gz
-rw-------  1 root root     0 2012-03-03 07:59 term.log
-rw-------  1 root root  4536 2011-01-17 11:42 term.log.10.gz
-rw-------  1 root root  6103 2010-10-16 23:53 term.log.11.gz
-rw-------  1 root root   797 2012-03-02 18:51 term.log.1.gz
-rw-------  1 root root   404 2012-01-26 10:39 term.log.2.gz
-rw-------  1 root root   394 2012-01-23 16:17 term.log.3.gz
-rw-------  1 root root   802 2011-07-15 09:48 term.log.4.gz
-rw-------  1 root root   711 2011-06-05 14:36 term.log.5.gz
-rw-------  1 root root  1232 2011-05-19 15:42 term.log.6.gz
-rw-------  1 root root   568 2011-04-04 14:16 term.log.7.gz
-rw-------  1 root root  3195 2011-02-02 00:03 term.log.8.gz
-rw-------  1 root root   466 2011-01-18 22:51 term.log.9.gz

/var/log/ConsoleKit:
total 52
drwxr-xr-x  2 root root  4096 2012-05-02 12:03 .
drwxr-xr-x 15 root root  4096 2012-05-21 13:56 ..
-rw-r--r--  1 root root 12485 2012-05-21 13:59 history
-rw-r--r--  1 root root  7614 2012-05-02 11:05 history.1
-rw-r--r--  1 root root   825 2012-04-04 11:35 history.2.gz
-rw-r--r--  1 root root   541 2012-02-27 20:06 history.3.gz
-rw-r--r--  1 root root  1709 2012-01-25 10:45 history.4.gz
-rw-r--r--  1 root root   871 2012-01-02 10:48 history.5.gz
-rw-r--r--  1 root root  1424 2011-12-05 11:15 history.6.gz

/var/log/cups:
total 52
drwxr-xr-x  2 root root    4096 2012-05-21 13:35 .
drwxr-xr-x 15 root root    4096 2012-05-21 13:56 ..
-rw-r-----  1 root lpadmin    0 2011-02-04 23:13 access_log
-rw-r-----  1 root adm      122 2011-02-01 23:11 access_log.1.gz
-rw-r-----  1 root adm      106 2011-01-17 11:53 access_log.2.gz
-rw-r-----  1 root adm      170 2010-10-08 21:54 access_log.3.gz
-rw-r-----  1 root adm      327 2012-05-21 13:56 error_log
-rw-r-----  1 root adm      140 2012-05-21 13:26 error_log.1.gz
-rw-r-----  1 root adm      122 2012-05-20 11:20 error_log.2.gz
-rw-r-----  1 root adm      139 2012-05-16 11:04 error_log.3.gz
-rw-r-----  1 root adm      123 2012-05-11 11:31 error_log.4.gz
-rw-r-----  1 root adm      123 2012-05-04 10:55 error_log.5.gz
-rw-r-----  1 root adm      121 2012-05-02 11:04 error_log.6.gz
-rw-r-----  1 root adm      124 2012-04-27 17:49 error_log.7.gz

/var/log/dist-upgrade:
total 8
drwxr-xr-x  2 root root 4096 2010-07-01 16:31 .
drwxr-xr-x 15 root root 4096 2012-05-21 13:56 ..

/var/log/fsck:
total 16
drwxr-xr-x  2 root root 4096 2010-08-16 05:34 .
drwxr-xr-x 15 root root 4096 2012-05-21 13:56 ..
-rw-r-----  1 root adm    31 2010-08-16 05:34 checkfs
-rw-r-----  1 root adm    31 2010-08-16 05:34 checkroot
ls: cannot open directory /var/log/gdm: Permission denied

/var/log/installer:
total 556
drwxr-xr-x  2 root   root   4096 2010-10-08 01:02 .
drwxr-xr-x 15 root   root   4096 2012-05-21 13:56 ..
-rw-------  1 root   root   1282 2010-10-08 00:47 casper.log
-rw-------  1 root   root    149 2010-10-08 00:47 debug
-rw-r--r--  1 root   root 369499 2010-10-08 01:02 initial-status.gz
-rw-r--r--  1 root   root     59 2010-10-08 01:02 media-info
-rw-------  1 root   root  83372 2010-10-08 00:50 partman
-rw-------  1 syslog adm   86006 2010-10-08 01:02 syslog
-rw-------  1 root   root     16 2010-10-08 00:47 version

/var/log/news:
total 8
drwxr-xr-x  2 root   root 4096 2010-10-08 01:06 .
drwxr-xr-x 15 root   root 4096 2012-05-21 13:56 ..
-rw-r-----  1 syslog adm     0 2010-10-08 01:06 news.crit
-rw-r-----  1 syslog adm     0 2010-10-08 01:06 news.err
-rw-r-----  1 syslog adm     0 2010-10-08 01:06 news.notice

/var/log/samba:
total 84
drwxr-xr-x  3 root root 4096 2012-05-20 11:38 .
drwxr-xr-x 15 root root 4096 2012-05-21 13:56 ..
drwx------  4 root root 4096 2010-10-16 23:53 cores
-rw-r--r--  1 root root    0 2010-10-16 23:57 log.10.0.2.15
-rw-r--r--  1 root root    0 2010-10-16 23:57 log.127.0.1.1
-rw-r--r--  1 root root 1572 2010-10-17 00:00 log.amir-laptop
-rw-r--r--  1 root root    0 2011-05-19 16:51 log.__ffff_127.0.1.1
-rw-r--r--  1 root root 2179 2012-05-21 13:56 log.nmbd
-rw-r--r--  1 root root  484 2012-05-20 11:38 log.nmbd.1.gz
-rw-r--r--  1 root root  440 2012-05-16 11:18 log.nmbd.2.gz
-rw-r--r--  1 root root  443 2012-05-11 12:07 log.nmbd.3.gz
-rw-r--r--  1 root root  458 2012-05-02 12:04 log.nmbd.4.gz
-rw-r--r--  1 root root  438 2012-04-24 14:39 log.nmbd.5.gz
-rw-r--r--  1 root root  422 2012-04-18 13:59 log.nmbd.6.gz
-rw-r--r--  1 root root  423 2012-04-04 12:02 log.nmbd.7.gz
-rw-r--r--  1 root root 4644 2012-05-21 13:55 log.smbd
-rw-r--r--  1 root root  311 2012-05-20 11:20 log.smbd.1.gz
-rw-r--r--  1 root root  342 2012-05-16 11:04 log.smbd.2.gz
-rw-r--r--  1 root root  344 2012-05-11 11:31 log.smbd.3.gz
-rw-r--r--  1 root root  371 2012-05-02 11:04 log.smbd.4.gz
-rw-r--r--  1 root root  340 2012-04-24 14:13 log.smbd.5.gz
-rw-r--r--  1 root root  312 2012-04-18 13:35 log.smbd.6.gz
-rw-r--r--  1 root root  311 2012-04-04 11:34 log.smbd.7.gz

/var/log/speech-dispatcher:
total 8
drwxr-xr-x  2 speech-dispatcher root 4096 2010-04-15 09:04 .
drwxr-xr-x 15 root              root 4096 2012-05-21 13:56 ..

/var/log/unattended-upgrades:
total 8
drwxr-xr-x  2 root root 4096 2010-04-29 11:02 .
drwxr-xr-x 15 root root 4096 2012-05-21 13:56 ..

---

### Post by JKyleOKC on 2012-05-21
The most suspicious thing I see in that output is that there are 48 versions of "error.log" in the apache2 subdirectory, but the modification dates for them vary consistently. Since each file occupies a minimum of 4K bytes even though it may use less than 1/4 of the space, this amounts to about 192K of space -- and that's a far cry from the GB that went missing.

The /var/log/messages file, at more than 200K, might be worth looking at -- but again, it's not large enough to account for all the missing space either.

In general, it's usually safe to delete log files with suffixes greater than ".7" since that will keep a week's worth of history, which is nice to have if you discover you've been invaded. Those error.log files in apache2 go back more than a month! It would also be a good idea to have a look at them and find out what is causing so many of them to exist...

---

