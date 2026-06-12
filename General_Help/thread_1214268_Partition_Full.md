---
title: "Partition Full?"
date: 2009-07-15
forum: General Help
---

### Post by Buuntu on 2009-07-15
Hi, 
I just copied an old partition into some unallocated space (around 170 GBs) and now when I boot from that partition, it shows that it's full even though in reality there should only be around 12 GBs used.  I'm relatively new to Ubuntu so I'm not really sure what's wrong.  Help anyone?

---

### Post by michy99 on 2009-07-15
What is the output from these commands?```
sudo fdisk -l
df -h
```

---

### Post by Buuntu on 2009-07-16
gabriel@gabriel-desktop:~$ sudo fdisk -l
[sudo] password for gabriel: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72f78cac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15300   122897218+   7  HPFS/NTFS
/dev/sda2           36958       38913    15711570    5  Extended
/dev/sda3           15301       36957   173959852+  83  Linux
/dev/sda5           38588       38891     2441848+  83  Linux
/dev/sda6           38892       38913      176683+  82  Linux swap / Solaris
/dev/sda7           38566       38587      176683+  82  Linux swap / Solaris
/dev/sda8           36958       37901     7582617   83  Linux
/dev/sda9           38200       38261      497983+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e54133e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4864    39070048+   7  HPFS/NTFS
gabriel@gabriel-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             7.2G  6.7G  102M  99% /
tmpfs                 1.3G     0  1.3G   0% /lib/init/rw
varrun                1.3G  200K  1.3G   1% /var/run
varlock               1.3G     0  1.3G   0% /var/lock
udev                  1.3G  168K  1.3G   1% /dev
tmpfs                 1.3G   76K  1.3G   1% /dev/shm
lrm                   1.3G  2.2M  1.3G   1% /lib/modules/2.6.28-13-generic/volatile

---

### Post by Buuntu on 2009-07-16
any ideas?

---

### Post by jms1989 on 2009-07-16
try clearing your logs and apt archives.

you can clear your apt archives by opening synaptic and going from there.

to clear the logs you'll need to run sudo nautilus and navigate to /var/log and delete the old .gz files. if the origional log files are bigger than say 20mb, delete them but remember to create a blank file of the same filename to avoid potential problems.

---

### Post by jms1989 on 2009-07-16
oh, you can safely delete dmesg, syslog, and debug but create a empty file afterwards.

---

### Post by raymondh on 2009-07-16
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by Buuntu on 2009-07-17
Thanks I think I fixed it with your link to recovering lost space.  Apparently I just had to run this command:

sudo resize2fs -p /dev/sda3

That updated the partition table I guess.

Thanks for all of your help!

---

### Post by raymondh on 2009-07-17
> **Buuntu said:**
> Thanks I think I fixed it with your link to recovering lost space.  Apparently I just had to run this command:

sudo resize2fs -p /dev/sda3

That updated the partition table I guess.

Thanks for all of your help!

Congratulations and you're welcome.

Happy Ubuntu-ing :)

---

