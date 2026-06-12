---
title: "Generic File System Question"
date: 2010-07-21
forum: General Help
---

### Post by MikeyDL on 2010-07-21
Just starting to get into more serious usage on Ubunu and moving away from windows.  But I had a question on a file system concept that I wasn't sure about.  In windows if you have two physical drives you can create to separate drive letters or add the second drive as an extended drive (one logical drive).  In linux everything is mounted under one file system.  If you add a second drive to a linux system does the new drive get added to the computer as an extended drive?  How do you manage where drive space issues in linux when everything is mounted to one file system?

---

### Post by rubylaser on 2010-07-21
If you add a separate drive, it's not part of the same "filesystem", it can have it's own different filesystem if you like (ext4, xfs, btrfs, etc).  The only thing it will have is a mount point that's part of the /.  So, my OS install drive may be formatted with ext4 ( / ), and I could have a separate drive with xfs mounted at ( /var/new_drive ).  

As and example, if you hook a thumb drive up to your computer, it will mount at /media/<uuid_of_drive> ,  it is now part of the / file tree, but likely is formatted as FAT.  I hope that explained it okay.

---

### Post by bodhi.zazen on 2010-07-21
See if this link helps : 

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

---

### Post by MikeyDL on 2010-07-21
Great guide!! explained allot of basic stuff I needed to make sure I knew more about.  Couple of inquiries on this topic that I'm still a little fuzzy about.

the /dev/sda drives are regular permanent internal hard drives

the /dev/sdb drives are the external portable drives?  Also those drives get a mount entry under /media as well as the /dev entry?

On my system drive there are three partitions sda1 for my main drive storage (primary), sda2 for an extended partition and sd5 for the swap (since it's 5 it much be an extended partition).  Is the extended 1.5gb partition (or sda2) the mandatory root partition?

Adding a 2nd physical drive will be added as a primary or extended partition, in my case possibly sd3 or sd4.  

All my current program install in /home/user or /usr/bin and those would by physically located on the first hard drive.  If i ran out of room on the primary hard drive then I could change the mount point for programs such as /usr/bin over to a new drive if needed.

Also if a 2nd physical drive was added would there be a seperate extended (i.e. root) and swap partition created when I added it?

---

### Post by bodhi.zazen on 2010-07-21
The order of drives in terms of sda , sdb , sdc is somewhat arbitrary, and can change.

Because of this fstab now uses UUID

---

