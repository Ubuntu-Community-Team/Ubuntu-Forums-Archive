---
title: "Simple partition question - Ubuntu 10.04"
date: 2012-03-22
forum: General Help
---

### Post by Marty4344 on 2012-03-22
Im trying to mount a second hard drive in ubuntu at boot, the hard drive was new so I had to create the partition. 

I created the partition to use the whole drive so here is the reading for fdisk

/dev/sdb1 ID:83 System: Linux

The partition is going to be used as a dump for zoneminder events and logs and will be shared over the network via samba

the location I want it mounted is 

/home/zoneminder/Desktop/ZoneMinder/

However when I try to mount the partion I cannot mount it, and when I try to automatically mount it at boot in fstab it wont boot it and I have to press S to skip it during boot.

When I try and mount it I get this error.  Also I want to mount it so other users via samba have access to it

wrong fs type, bad option, bad superblock on /dev/sdb1

Im not sure what it is im doing wrong.

---

### Post by dave2001 on 2012-03-22
Hi Marty, sorry your having trouble.

> **Marty4344 said:**
> 

wrong fs type, bad option, bad superblock on /dev/sdb1



First make sure your filesystem is ok. This command will run a filesystem check of the drive and attempt to repair any problems found.
```
sudo e2fsck /dev/sdb1 
```The, try the following to mount the drive manually.

First create a directory for the mount point 
```
sudo mkdir /home/zoneminder/Desktop/ZoneMinder
```Then mount the disk
```
sudo mount /dev/sdb1 /home/zoneminder/Desktop/ZoneMinder
```

If this works, then we can go about creating an fstab entry to automount at boot.

---

### Post by Marty4344 on 2012-03-22
Its telling me 

Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2 file ssystem.

---

### Post by Marty4344 on 2012-03-22
Also I just made the parition so it should be empty.

---

### Post by oldfred on 2012-03-22
If you have no data to salvage, I might just reformat it. Is it really ext2, any larger partition should be ext4 or ext3 so you have a journal.

If you want to try to run some repairs.

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by Cheesemill on 2012-03-22
You have created a linux partition but have you actually formatted it yet?

---

