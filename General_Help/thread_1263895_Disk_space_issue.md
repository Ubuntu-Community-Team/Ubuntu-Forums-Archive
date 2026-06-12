---
title: "Disk space issue"
date: 2009-09-11
forum: General Help
---

### Post by lexe-cc on 2009-09-11
Hi,

I just ordered a new hdd for my laptop. It works fine except for this "small" issue. I just copied all my music from my old disk to the new disk. After this was done i noticed that there's some disk space missing. (see screenshot) Could anybody tell me where the 9gb has gone? Is this something inherent to the filesystem or is there definately 9gb "lost" on my hdd. 

Thanks in advance!
Kind regards,
Lexe

screenshot:
[http://users.telenet.be/frederikcornillie/tmp/Screenshot3.png](http://users.telenet.be/frederikcornillie/tmp/Screenshot3.png)

---

### Post by Liolikas on 2009-09-11
Look into disk with fdisk -l or gparted and post here they both more informative.

---

### Post by DaithiF on 2009-09-11
Hi,
i see its an ext filesystem, so most likely its the fact that 5% space is reserved by the system.  If this is an extra drive you're using for data (ie. its not the system drive where '/' is mounted), then its fine to remove this 5% reserve.

to confirm the issue:
```
sudo tune2fs /dev/YOURPARTITION

```where YOURPARTITION sdb1 or similar -- see sudo fdisk -l if you need help identifying which parition this is.
in the output from tune2fs, look for these lines:
```
Reserved block count:     1025348
...
Block size:               4096

```the first x the second will be your reserved space.

to reduce the % of the partition you want reserved, 
sudo tune2fs -m X /dev/YOURPARTITION
where X is a number ... 0, 1, 2, etc

cheers
d

---

### Post by lexe-cc on 2009-09-11
First of all, thanks for your help :)

On my laptop drive i have 3 partitions:
1) windows (not used that much, only for work)
2) ubuntu 9.04
3) the drive i mentioned before

So i guess it's the drive where "/" is mounted. So this means i can't use the 9gb right?

If this is the case i'll leave it this way. I just wondered where on earth my 9gb did go :)

Greets

---

### Post by DaithiF on 2009-09-11
sounds more like partition 2 would be the one with '/' mounted, but you can check by running 
```
df
```
and checking out the last column (Mounted on)

To be honest, given the size of modern disks the 5% reserved space is probably overkill, so if you are running short of space, its fine to reduce the % even on the '/' partition.

---

### Post by lexe-cc on 2009-09-12
lexe@lexe-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             28834744   3316536  24053484  13% /
tmpfs                   512612         0    512612   0% /lib/init/rw
varrun                  512612        92    512520   1% /var/run
varlock                 512612         0    512612   0% /var/lock
udev                    512612       160    512452   1% /dev
tmpfs                   512612        76    512536   1% /dev/shm
lrm                     512612      2192    510420   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda4            180314184  66235976 104918752  39% /media/share
/dev/sda1             30716248   2725028  27991220   9% /media/windows

This is the output of df. Where can i change the 5%?

---

### Post by DaithiF on 2009-09-12
looks like /dev/sda4 is the 180GB ext3 paritition you posted the screen shot for, so
```
sudo tune2fs -m 0 /dev/sda4

```will set the reserved space to 0%

---

