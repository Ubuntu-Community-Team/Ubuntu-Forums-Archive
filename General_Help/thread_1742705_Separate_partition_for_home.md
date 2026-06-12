---
title: "Separate partition for /home?"
date: 2011-04-29
forum: General Help
---

### Post by lycee on 2011-04-29
I have installed various distros/releases of linux over the past few days and have read of a few people keeping separate partitions for their /home folders. I have a few questions:

1) How is this done? I assume /home is installed with the OS and would always be on the OS partition.

2) Can I repartition the drive even though I am already installed to allocate space or would I have to start from scratch, create the partitions, and reinstall the OS?

3) How much space would one need for a home folder? Majority of hdd right?

Thanks in advance.

---

### Post by kartabosh on 2011-04-29
well you can do it any time, just shrink whatever drive you have and create a new partition from the unallocated space
then mount that as your /home partition
i've seen many people do that but i prefer to create a /home/X partition (replace x with media or whatever you want it), that way the configuration and everything stays on the ubuntu partition (where it belongs) and my personal stuff is on /home/media (or whatever) which is a totally different partition that i can use with other distros without messing the configurations between them
after you repartition the space you have to edit your /etc/fstab file

mine looks like 
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=48ce52cf-3c1a-485e-bc94-6180292d8db1 /               ext4    errors=remount-ro 0       1
UUID=1246e7ad-0070-463f-b238-a3ae30bfb34e /boot           ext2    defaults        0       2
UUID=eb5dda6d-36e7-4d54-bcc8-48629504fed1 /home/media     ext4    defaults        0       2
UUID=9ecc4a38-0628-490f-907c-28c9bf2552aa /home/stuff     ext4    defaults        0       2
UUID=4074576574575D2A /not-linux/extra ntfs    defaults,umask=007,gid=46 0       0
UUID=4E8099E18099CFB7 /not-linux/system ntfs    defaults,umask=007,gid=46 0       0
UUID=c63cece6-8625-477a-8530-c812f6d6000b none            swap    sw              0       0

```
as you can see i have various mount points 
/boot (on it's own partition) for my boot files 
/home/media (on it's own partition) for my media files
/home/stuff (on it's own partition) for my personal files 
/not-linux/extra for my windows extra files
/not-linux/system for my windows system files

so basically what you do is after you create the new partition you right click the new partition and check it's uuid 

[[IMG]http://img832.imageshack.us/img832/4152/0026r.png[/IMG]]("http://i.imgur.com/otE8u.png")

once you have that you go in your fstab file and add this line 

```
UUID=*PLACE UUID HERE* /*PLACE MOUNT POINT HERE*/     ext4    defaults        0       2
```
obviously replace *PLACE UUID HERE* with the uuid and /*PLACE MOUNT POINT HERE*/ with /home/ or /home/whatever
assuming the new partition is a ext4 file system,
now you reboot and when you log in the file should be there (if you selected a non-default mount point such as /home/media you must first create the /home/media folder then make that mount point)

---

### Post by Lars Noodén on 2011-04-29
> **lycee said:**
> I have installed various distros/releases of linux over the past few days and have read of a few people keeping separate partitions for their /home folders. I have a few questions:

1) How is this done? I assume /home is installed with the OS and would always be on the OS partition.


Usually during the initial installation.

> **lycee said:**
> 
2) Can I repartition the drive even though I am already installed to allocate space or would I have to start from scratch, create the partitions, and reinstall the OS?


You can boot the install cd and use it to resize the existing partition and then make a new /home.  You'll need to juggle a little to transfer the old data over to the new partition.

> **lycee said:**
> 
3) How much space would one need for a home folder? Majority of hdd right?


That depends on how much you need.  I'd leave around 18 GB for Ubuntu just so there's ample extra space for programs.  You won't need that much but it's good to have.

---

### Post by Bucky Ball on 2011-04-29
Moving the data from the original /home then deleting that directory is not as easy as everyone seems to be insinuating. (You're right; /home is in one big partition with / and /swap with an 'automatic' install.)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Your personal data and settings are stored in your original /home partition and if you simply move the data from there to your new, separate /home partition, then delete the old one, chaos will rein. The system is still pointed at the old /home and it's not there. You need to tell the OS where the new /home is for oh so many reasons and that won't happen by simply creating a separate /home partition, moving data from the old /home, deleting it, and then rebooting. The system won't automagically know to look at the new location for your settings ... ;)

---

### Post by lycee on 2011-04-29
I appreciate all the advice. Should be no problem now.

---

