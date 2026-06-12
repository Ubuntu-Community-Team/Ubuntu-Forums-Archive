---
title: "Low memory in /boot"
date: 2011-04-09
forum: General Help
---

### Post by jfreak_ on 2011-04-09
Getting this error message


My /boot is 100mb only. Only the kernel versions .29 and .30 are present. I have had this problem before but then by cleaning up the older versions it would get solves , but now it isn't. Help.

---

### Post by f1tz on 2011-04-09
You could try resizing your boot partition to something a bit larger? Use one of the LiveCDs with a partition manager on it, make sure stuff isnt mounted and dont format it. Either that or remove one of the old kernals.

---

### Post by ajgreeny on 2011-04-09
Why a separate /boot partition?  It has never really made sense to me, but I am sure there must be good reasons for doing so.

Perhaps to solve this you just need to enlarge the partition with gparted from a live CD, but back up everything first as I am shooting blind here, never having needed to do anything similar.

---

### Post by jfreak_ on 2011-04-09
> **f1tz said:**
> You could try resizing your boot partition to something a bit larger? Use one of the LiveCDs with a partition manager on it, make sure stuff isnt mounted and dont format it. Either that or remove one of the old kernals.

I removed two of my old kernels but to no effect.

---

### Post by f1tz on 2011-04-09
> I removed two of my old kernels but to no effect. 	
You may be able to squeeze a bit more out: sudo apt-get autoclean

I reckon your boot partition is a bit too small, back it up, then try using gparted from a live CD to enlarge the partition. The other option is moving it, this thread seems to deal with something similar: [http://ubuntuforums.org/showthread.php?t=1689277](http://ubuntuforums.org/showthread.php?t=1689277)

---

### Post by plucky on 2011-04-09
> **jfreak_ said:**
> I removed two of my old kernels but to no effect.

How did you do the removal?

If you used synaptic then you should recover the space,but if you deleted  the files,maybe they are still taking up space on the partition as trash.

What does ```
df -h
ls -lh /boot
``` show you?

---

### Post by jfreak_ on 2011-04-09
> **plucky said:**
> How did you do the removal?

If you used synaptic then you should recover the space,but if you deleted  the files,maybe they are still taking up space on the partition as trash.

What does ```
df -h
ls -lh /boot
``` show you?

```

jfreak@jfreak-linuxbox:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              11G  6.8G  3.7G  65% /
none                  462M  304K  462M   1% /dev
none                  469M  188K  469M   1% /dev/shm
none                  469M   84K  469M   1% /var/run
none                  469M     0  469M   0% /var/lock
none                  469M     0  469M   0% /lib/init/rw
/dev/sda1              92M   85M  2.0M  98% /boot
/dev/sda7             135G   60G   68G  47% /home
/dev/sdb1             7.5G  5.9G  1.7G  79% /media/4A5D0A9A5A34A26E
jfreak@jfreak-linuxbox:/$ 
jfreak@jfreak-linuxbox:/$ ls -lh /boot
total 75M
-rw-r--r-- 1 root root 637K 2010-11-24 19:27 abi-2.6.32-26-generic
-rw-r--r-- 1 root root 637K 2010-12-02 06:18 abi-2.6.32-27-generic
-rw-r--r-- 1 root root 637K 2011-01-11 06:48 abi-2.6.32-28-generic
-rw-r--r-- 1 root root 637K 2011-02-12 01:26 abi-2.6.32-29-generic
-rw-r--r-- 1 root root 637K 2011-03-02 07:57 abi-2.6.32-30-generic
-rw-r--r-- 1 root root 114K 2010-11-24 19:27 config-2.6.32-26-generic
-rw-r--r-- 1 root root 114K 2010-12-02 06:18 config-2.6.32-27-generic
-rw-r--r-- 1 root root 114K 2011-01-11 06:48 config-2.6.32-28-generic
-rw-r--r-- 1 root root 114K 2011-02-12 01:26 config-2.6.32-29-generic
-rw-r--r-- 1 root root 114K 2011-03-02 07:57 config-2.6.32-30-generic
drwxr-xr-x 3 root root 6.0K 2011-02-09 01:15 grub
-rw-r--r-- 1 root root  15M 2010-12-06 01:44 initrd.img-2.6.32-26-generic
-rw-r--r-- 1 root root  15M 2011-01-23 00:22 initrd.img-2.6.32-27-generic
-rw-r--r-- 1 root root  15M 2011-03-04 20:31 initrd.img-2.6.32-28-generic
drwx------ 2 root root  12K 2010-05-23 00:13 lost+found
-rw-r--r-- 1 root root 157K 2010-03-23 15:07 memtest86+.bin
-rw-r--r-- 1 root root 1.7M 2010-11-24 19:27 System.map-2.6.32-26-generic
-rw-r--r-- 1 root root 1.7M 2010-12-02 06:18 System.map-2.6.32-27-generic
-rw-r--r-- 1 root root 1.7M 2011-01-11 06:48 System.map-2.6.32-28-generic
-rw-r--r-- 1 root root 1.7M 2011-02-12 01:26 System.map-2.6.32-29-generic
-rw-r--r-- 1 root root 1.7M 2011-03-02 07:57 System.map-2.6.32-30-generic
-rw-r--r-- 1 root root 1.2K 2010-11-24 19:30 vmcoreinfo-2.6.32-26-generic
-rw-r--r-- 1 root root 1.2K 2010-12-02 06:20 vmcoreinfo-2.6.32-27-generic
-rw-r--r-- 1 root root 1.2K 2011-01-11 06:50 vmcoreinfo-2.6.32-28-generic
-rw-r--r-- 1 root root 1.2K 2011-02-12 01:27 vmcoreinfo-2.6.32-29-generic
-rw-r--r-- 1 root root 1.2K 2011-03-02 07:59 vmcoreinfo-2.6.32-30-generic
-rw-r--r-- 1 root root 3.9M 2010-11-24 19:27 vmlinuz-2.6.32-26-generic
-rw-r--r-- 1 root root 3.9M 2010-12-02 06:18 vmlinuz-2.6.32-27-generic
-rw-r--r-- 1 root root 3.9M 2011-01-11 06:48 vmlinuz-2.6.32-28-generic
-rw-r--r-- 1 root root 3.9M 2011-02-12 01:26 vmlinuz-2.6.32-29-generic
-rw-r--r-- 1 root root 3.9M 2011-03-02 07:57 vmlinuz-2.6.32-30-generic
jfreak@jfreak-linuxbox:/$ 

```


However according to synaptic .26, .27, .28, .29 are not installed

---

### Post by jfreak_ on 2011-04-10
Got it , had to remove linux-image.   silly me. :-)

---

