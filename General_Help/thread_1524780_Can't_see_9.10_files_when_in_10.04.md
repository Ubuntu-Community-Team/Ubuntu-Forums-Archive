---
title: "Can't see 9.10 files when in 10.04??"
date: 2010-07-05
forum: General Help
---

### Post by steve509 on 2010-07-05
Hello again guys, i'm now running a dual boot with ubuntu 9.10 and 10.04 and am wondering, shouldn't i be able to get to see the files in 9.10 when in 10.04 and see file system in 10.04 when in 9.10??? how do I fix this? I've been running 9.10 for about 3 to 4 months now and 10.04 for only 2 weeks and would like to transfer or copy files over...any suggestion??

Thanks
steve509

---

### Post by btindie on 2010-07-05
I'm guessing that you installed Lucid on another partition? In which case to be able to access your files on the other install you need to mount it's partition.
 
To see your currently mounted partitions type
```
mount | grep ^/
```
you're current installed partition is likely to be something like /dev/sdaX (where X is a number)
 
To list the available partitions type
```
sudo /sbin/fdisk -l
```
 
Look at the partitions listed, there should be a few with the type of Linux. It's not the one that was listed with the first command above you want but the other. Again it'd be something like /dev/sdaX.
 
Create a mount point for the partition
```
sudo mkdir /mnt/karmic
```
 
Mount the partition
```
sudo mount /dev/sdaX /mnt/karmic
```
 
Your karmic installation will then be accessible under */mnt/karmic*.

---

### Post by steve509 on 2010-07-06
btindie, thank you for your help, I can now see the file system on my other partition.

steve509

---

### Post by btindie on 2010-07-06
Just to add, if you want to be able to access that partition after a reboot then you'll need to add an entry to */etc/fstab*. So from my above example the entry you'd add would look like:
```
/dev/sdX      /mnt/karmic        defaults       0  0
```

---

### Post by steve509 on 2010-07-08
Again thank you for all your help, it is so greatly appreciated

---

