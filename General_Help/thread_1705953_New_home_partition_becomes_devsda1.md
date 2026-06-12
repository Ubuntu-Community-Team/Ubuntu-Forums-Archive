---
title: "New /home partition becomes /dev/sda1"
date: 2011-03-13
forum: General Help
---

### Post by hamartia on 2011-03-13
I had my /home partition on a separate ide drive which I have recently replaced with a terabyte SATA drive.

1. I have successfully cloned from original to new (clonezilla), and increased the size of the partition on the new using gparted. I understand that this would not cause data loss. Am I correct?

2. Whereas my os hd used to be /dev/sda1 and my /home ide drive was /dev/sdb1, gparted recognises my terabyte SATA drive now as /dev/sda1, and my os hd as /dev/sdb1:

```
hamartia@carrera:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              15G  4.4G  9.7G  31% /
none                  735M  304K  734M   1% /dev
none                  739M  268K  738M   1% /dev/shm
none                  739M  288K  738M   1% /var/run
none                  739M     0  739M   0% /var/lock
none                  739M     0  739M   0% /lib/init/rw
/dev/sda1             1.4T  188G  1.1T  15% /home
hamartia@carrera:~$ 
```My fstab however, shows this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1151aa43-ec8f-4c62-b351-2a6e3144c4a8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
#UUID=f29becee-2eea-4f82-8526-93c430658cc6 /home           ext4    defaults        0       2
LABEL=terabyte_home /home    ext4   defaults
# swap was on /dev/sda5 during installation
UUID=43076bb5-256b-4424-8db6-d814e1ea2766 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```Is this switching of /dev/sda1 and /dev/sdb1 a problem, and if so, what should I do?

Many thanks for your help.

---

### Post by skada on 2011-03-13
Doesn't seem to be problem.
Try ```
sudo blkid
``` and check the UUID's

---

