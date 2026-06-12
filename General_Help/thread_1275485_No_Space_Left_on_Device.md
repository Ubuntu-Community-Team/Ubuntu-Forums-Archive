---
title: "No Space Left on Device"
date: 2009-09-25
forum: General Help
---

### Post by DarkMage2303 on 2009-09-25
I installed Ubuntu inside Windows XP, I'm trying to install Partition Manager and I get the error "No Space on Disk".

Screenshot:

[IMG]http://i244.photobucket.com/albums/gg17/DarkMage2303/NoSpaceOnDisk.jpg[/IMG]

When I go to computer:/// it says that this filesystem has 9.2GB space free, is there any way to fix this?

---

### Post by akakingess on 2009-09-25
I am by no means an expert or even knowledgeable on these matters, but how much space did you give to Ubuntu under Windows, and is there a chance that it is running out of room?  Is that why you are trying to install partition manager? To give the Ubuntu partition more room? If so, maybe you can boot off of a live CD and run partition manager from there, I don't know, remember I am not an expert, especially on Wubi installs.

---

### Post by wojox on 2009-09-25
What does:

```
df -h
```

Show you?

---

### Post by egalvan on 2009-09-25
> 
I installed Ubuntu inside Windows XP,
Installing "inside Windows" is called Wubi.

it does NOT create a partition for Linux.
it creates a Windows file inside the Windows file system.

Partition Editor (gparted) will NOT be able to re-size that file.

It CAN be used to re-size an XP partition, just be sure to defrag it well, before you start gparted.

And while gparted can be used to VIEW partitions,
the partition must be un-mounted before you can perform any operations on it.

Which means gparted inside a Wubi install CANNOT be used to operate on the holding partition.

You need a LiveCD to move/re-size/delete/etc.

Ubuntu LiveCD
PartedMagic LiveCD
SuperGRUB LiveCD

for examples

---

### Post by egalvan on 2009-09-25
oops, double post...

---

### Post by DarkMage2303 on 2009-09-25
What I'm wanting to do is create a new partition using Partition Manager so i can use LVPM to give Ubuntu its own partition.

I gave Ubuntu 15GB, it has 9.2GB free space. 

> filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G  3.0G  9.2G  25% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  216K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  404K  505M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdb1             466G  238G  228G  52% /media/FreeAgent Drive
/dev/loop0             13G  3.0G  9.2G  25% /media/loop0
/dev/loop0             13G  3.0G  9.2G  25% /media/loop0_
/dev/sda1              28G   28G     0 100% /host


EDIT: My c:\ for Windows is full.. didn't realise that. I'm deleting files from the /host/ folder now to clean up some space.

Now, when I try to boot using Partition Manager (when Ubuntu is about to load and I have 10 secs to press ESC to see the menu) I am getting "Error 23: Error while parsing number"

Anyone know how to fix this?

---

