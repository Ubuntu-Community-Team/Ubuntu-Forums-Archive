---
title: "Unable to install updates!"
date: 2009-07-24
forum: General Help
---

### Post by Theory5 on 2009-07-24
I have just finished sucessfully finished installing ubuntu, and I restarted and an updates window popped up so I try to install the updates. I tried to cancel it when it seemed to have stopped, and It told me that when I canceled it a few packages did not get installed and then when I tried to install it again it told me all of the 352 megabytes in my / folder was full. That is wierd because the entire partition is 100 GB's. 

Another problem is that sometimes I get the message: Failed to run so and so as users root, unable to copy the user's Xauthorization File.
Please help.

---

### Post by philcamlin on 2009-07-24
post output of 

sudo fdisk -l  :popcorn:

---

### Post by merlinus on 2009-07-24
```
df -h
```

will show usage.

---

### Post by Theory5 on 2009-07-24
here is what I get when I enter those two commands. For somereason firefox will not start up either, I have a lot of problems with this OS :-(

theory@theory-laptop-ubuntu:~$ sudo fdisk -l
[sudo] password for theory: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b330707

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       45089   362176368+   7  HPFS/NTFS
/dev/sda2           45090       45415     2618595    5  Extended
/dev/sda3           59145       60801    13306880    7  HPFS/NTFS
/dev/sda4           45416       58969   108872505   83  Linux
/dev/sda5           45090       45393     2441848+  83  Linux
/dev/sda6           45394       45415      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order
theory@theory-laptop-ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  100K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  176K  1.8G   1% /dev
tmpfs                 1.8G  588K  1.8G   1% /dev/shm
lrm                   1.8G  2.7M  1.8G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   20K 1004K   2% /tmp
theory@theory-laptop-ubuntu:~$


another thing is that gparted is not on ubuntu anymore, whereas it was on the livecd.

---

### Post by plucky on 2009-07-24
```
theory@theory-laptop-ubuntu:~$ df -h
Filesystem Size Used Avail Use% Mounted on
[color=red]/dev/sda5 2.3G 2.3G 0 100% /[/color]
tmpfs 1.8G 0 1.8G 0% /lib/init/rw
varrun 1.8G 100K 1.8G 1% /var/run
varlock 1.8G 0 1.8G 0% /var/lock
udev 1.8G 176K 1.8G 1% /dev
tmpfs 1.8G 588K 1.8G 1% /dev/shm
lrm 1.8G 2.7M 1.8G 1% /lib/modules/2.6.28-11-generic/volatile
overflow 1.0M 20K 1004K 2% /tmp
```

The highlighted line is your problem as there is no space on the / system partition.

What is the other linux partition used for ```
/dev/sda4 45416 58969 108872505 83 Linux
``` which is approx 100G.Did you mean to use it as your /home partition?

> another thing is that gparted is not on ubuntu anymore, whereas it was on the livecd. 

You have to install gparted after the installation,but it is more useful on the Live CD.

You need to use the Live CD to expand your / system partition as you cannot resize a mounted partition.

If /dev/sda4 is not being used at the moment,you can shrink it and expand the /dev/sda5 partition.


Good Luck

---

### Post by merlinus on 2009-07-24
Excellent how-to for this problem posted by a forum member:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by Theory5 on 2009-07-24
> **plucky said:**
> ```
theory@theory-laptop-ubuntu:~$ df -h
Filesystem Size Used Avail Use% Mounted on
[color=red]/dev/sda5 2.3G 2.3G 0 100% /[/color]
tmpfs 1.8G 0 1.8G 0% /lib/init/rw
varrun 1.8G 100K 1.8G 1% /var/run
varlock 1.8G 0 1.8G 0% /var/lock
udev 1.8G 176K 1.8G 1% /dev
tmpfs 1.8G 588K 1.8G 1% /dev/shm
lrm 1.8G 2.7M 1.8G 1% /lib/modules/2.6.28-11-generic/volatile
overflow 1.0M 20K 1004K 2% /tmp
```

The highlighted line is your problem as there is no space on the / system partition.

What is the other linux partition used for ```
/dev/sda4 45416 58969 108872505 83 Linux
``` which is approx 100G.Did you mean to use it as your /home partition?



You have to install gparted after the installation,but it is more useful on the Live CD.

You need to use the Live CD to expand your / system partition as you cannot resize a mounted partition.

If /dev/sda4 is not being used at the moment,you can shrink it and expand the /dev/sda5 partition.


Good Luck
oh s**t, it mustive thrown ubuntu on  one of my unallocated 1-2 GB blocks in my hdd when I selected "install ubuntu alongside windows" The bigger block was supposed to be the one it installed on. I will look at that post and hopefully fix it.

YAY I belive that its fixed now. Thanks for posting that tutorial for expanding my partitions.

---

