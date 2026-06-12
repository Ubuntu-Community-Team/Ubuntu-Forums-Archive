---
title: "Cloning ubuntu hard drive"
date: 2012-01-17
forum: General Help
---

### Post by cadogan32 on 2012-01-17
I'm trying to clone my ubuntu 60gb hard drive to my new laptop's 300gb hard drive.I have read clonezilla works good for cloning,but was thinking of also trying the DD command.Any problems with cloning a hard drive with 2 different Gb sizes?What would be the best route for getting this done right?thanks

---

### Post by Mark Phelps on 2012-01-17
I don't actually use Clonezilla to clone; instead, I use it to do image backups.  But I believe that when you "clone" a disk, it copies the exact contents to the new drive.  Thus, the new drive will be partitioned the same as the existing drive.

I don't believe there is a resize option when cloning.

---

### Post by gsgleason on 2012-01-17
What if you:

1. partition the new drive
2. use dd to clone the filesystem (/dev/sda1) to new drive (/dev/sdb1)
3. extend the filesystem size to fill the partition.

This is just an idea.  It can't hurt.  Just don't get rid of that older drive any time soon.

Also, what if you boot to a rescue/live CD and just partition the new one and use rsync to copy the entire contents, preserving ownership and permission, of the old to the new?

---

### Post by oldfred on 2012-01-17
I believe in clean installs and using rsync to copy /home and maybe a few other settings to the new drive. Ends up doing a major houseclean as all older info is housecleaned. You can make a list of installed applications and reinstall easily.

See this thread where a user used dd and is having size issues. dd is intended for copy to the same size only. You also will have the same UUID which is only ok if you do not want to use old drive. 

[http://ubuntuforums.org/showthread.php?t=1909081](http://ubuntuforums.org/showthread.php?t=1909081)

My backup plan is just a reinstall and restore. So my backups include (hopefully) everything I need to restore:
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by imachavel on 2012-01-17
here is my partition table:

sudo fdisk -l
[sudo] password for danel: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ded99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    95379456   658579455   281600000   83  Linux
/dev/sda2       658581502   976771071   159094785    5  Extended
/dev/sda5       853129216   924809215    35840000   82  Linux swap / Solaris
/dev/sda6       658581504   776222719    58820608   83  Linux
/dev/sda7       776224768   781449215     2612224   82  Linux swap / Solaris

Partition table entries are not in disk order



so if I had a hard drive I wanted to clone to a new build I had just made, I would use this?:

sudo dd if=/dev/sda of=/dev/sdc

reference:

[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)

assuming sdc is the new drive I've connected with a usb transfer device??

Then just fix the drivers once I pop the hard drive into the new build? Weird I'd assume files backed up and a fresh install would just be much simpler. But then in a business environment, cloned and captured images are great to go I suppose, especially if you want to do an upgrade deployment. THen kvm comes into the picture, etc. etc. etc. domain d.n.s. settings captured instance blah blah

Anyway don't meant to derail the thread:popcorn:

---

### Post by Dngrsone on 2012-01-17
I have upgraded the drive on several laptops (in other words, always going from a smaller drive to a larger one) using CloneHD to copy bit-for-bit from one drive to the next.

Clonezilla should be able to do the same thing.  The advantage is that the installed OS(es) don't see any change.  It would be up to you to decide what to do with the extra unformatted drive space.

---

