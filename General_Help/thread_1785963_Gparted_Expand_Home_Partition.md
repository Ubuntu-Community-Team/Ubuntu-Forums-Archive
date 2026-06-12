---
title: "Gparted Expand Home Partition"
date: 2011-06-19
forum: General Help
---

### Post by mooreted on 2011-06-19
I have these partitions and somehow the install made my /home partition too small. I would like to make / about 20gb and the rest for /home but I can't seem to make it happen.


 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36473   292967424   83  Linux
/dev/sda2           36474       38914    19601409    5  Extended
/dev/sda5           36474       38297    14647296   83  Linux
/dev/sda6           38297       38914     4953088   82  Linux swap / Solaris


/dev/sda1             276G  6.7G  255G   3% /
none                  2.9G  696K  2.9G   1% /dev
none                  3.0G  1.4M  3.0G   1% /dev/shm
none                  3.0G  344K  3.0G   1% /var/run
none                  3.0G     0  3.0G   0% /var/lock
/dev/sdb1             466G  434G   33G  94% /mnt/music
/dev/sdc2             149G   74G   76G  50% /mnt/windows
/dev/sda5              14G  4.3G  8.9G  33% /home

---

### Post by wildmanne39 on 2011-06-19
> **mooreted said:**
> I have these partitions and somehow the install made my /home partition too small. I would like to make / about 20gb and the rest for /home but I can't seem to make it happen.


 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36473   292967424   83  Linux
/dev/sda2           36474       38914    19601409    5  Extended
/dev/sda5           36474       38297    14647296   83  Linux
/dev/sda6           38297       38914     4953088   82  Linux swap / Solaris


/dev/sda1             276G  6.7G  255G   3% /
none                  2.9G  696K  2.9G   1% /dev
none                  3.0G  1.4M  3.0G   1% /dev/shm
none                  3.0G  344K  3.0G   1% /var/run
none                  3.0G     0  3.0G   0% /var/lock
/dev/sdb1             466G  434G   33G  94% /mnt/music
/dev/sdc2             149G   74G   76G  50% /mnt/windows
/dev/sda5              14G  4.3G  8.9G  33% /home
Hi, you have to be very careful with changing partitions or you will end up with a system that will not boot. I am going to give you a link that will tell you how to partition.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by mooreted on 2011-06-19
I'm beginning to think it can't be done. I think it would be better to just have /home/mooreted on sda1 along with / and just get rid of the sda5 partition altogether. 

Now, if I can just figure out how to change the location of /home/mooreted.

The problem is, if I shrink sda1 which is a primary partition it leaves unallocated space and I can't expand sda5 into that space because sda5 is an extended partition. No matter what I do, I cannot make sda5 bigger.

---

### Post by dcstar on 2011-06-19
> **mooreted said:**
> I have these partitions and somehow the install made my /home partition too small. I would like to make / about 20gb and the rest for /home but I can't seem to make it happen.
........

You have to boot off a Live CD/USB, install **gparted** and use that to resize the partitions on the hard drive.

Once that is done you have to change the /etc/fstab file on the hard drive to reflect the new UUIDs of the / and /home partitions.

And you have to be VERY careful doing all of these things.

---

### Post by mooreted on 2011-06-19
Thanks for the help. I think I'm going to keep it simple and just create folder on sda1, make it user rw and put any big files in there. Any programs that create big data files I can symlink to a folder on the bigger partition.

---

### Post by wildmanne39 on 2011-06-19
> **mooreted said:**
> Thanks for the help. I think I'm going to keep it simple and just create folder on sda1, make it user rw and put any big files in there. Any programs that create big data files I can symlink to a folder on the bigger partition.Hi, your welcome, sorry it looks so complicated.

---

### Post by mooreted on 2011-06-19
> **wildmanne39 said:**
> Hi, your welcome, sorry it looks so complicated.

Not just complicated, dangerous. Could hose my whole system, of course I could just re-install, but it would be frustrating.

Thanks again.

---

### Post by mooreted on 2011-06-19
Just for kicks, I think I thought of a way that might work. Maybe I'll check it out one day just to test it:

--Back up everything first
--Shrink the primary partition
--Create a partition in the unused space
--Move /home to the new partition
--Remove the old /home partition
--Expand the new /home partition
--Reboot and pray

---

### Post by -kg- on 2011-06-19
> **mooreted said:**
> Just for kicks, I think I thought of a way that might work. Maybe I'll check it out one day just to test it:

--Back up everything first
--Shrink the primary partition
--Create a partition in the unused space
--Move /home to the new partition
--Remove the old /home partition
--Expand the new /home partition
--Reboot and pray

Shouldn't even be that hard.

> --Back up everything first

+1 - +1 - +1!

> --Shrink the primary partition

sda1 to 20 GB...that should be good.  Personally, I divert from there, though.

Once you've shrank sda1, the next step I would take is to expand sda2 (the Extended partition) into the free space that results from shrinking sda1.  Then extend sda5 into the free space in the Extended partition.

I'm pretty sure you won't have any problems with the above scenario.  I always like leaving Linux OSes and related partitions within Extended/Logical partitions.  That leaves Primary partition space for "other" OSes I might want to use that require at least one.  :p

I'm not particularly fond of using the UUID method for fstab...I much prefer using drive designations.  If the UUID of the partition changes, it's pretty easy to edit fstab from the LiveCD, though.

---

### Post by mooreted on 2011-06-20
I tried that and it wouldn't let me expand the extended partition into the unused space, I could only make the extended partition smaller.

I was using Puppy Linux's gparted. Maybe it has limitations.

---

### Post by psusi on 2011-06-20
> **dcstar said:**
> You have to boot off a Live CD/USB, install **gparted** and use that to resize the partitions on the hard drive.

Once that is done you have to change the /etc/fstab file on the hard drive to reflect the new UUIDs of the / and /home partitions.

And you have to be VERY careful doing all of these things.

Resizing partitions does not alter their UUID.

---

### Post by -kg- on 2011-06-21
> **mooreted said:**
> I tried that and it wouldn't let me expand the extended partition into the unused space, I could only make the extended partition smaller.

I was using Puppy Linux's gparted. Maybe it has limitations.

You shouldn't be able to make the Extended partition smaller...according to this, your extended partition is full:

> /dev/sda2 36474 38914 19601409 5 Extended
/dev/sda5 36474 38297 14647296 83 Linux
/dev/sda6 38297 38914 4953088 82 Linux swap / Solaris

Notice that the beginning of sda2 is 36474 and the end is 38914.  The beginning of sda5 (the first logical partition) is 36474 and the end of the swap partition (sda6) is 38914.  Since these two numbers equal the beginning/ending of the Extended partition, the Extended partition is full and you can't make it smaller.

Are you sure you were trying to expand sda2, or were you trying to expand sda5?  You can't extend a logical partition beyond the boundaries of the Extended partition which contains it.

You might make this mistake if you try to click on the Extended partition in the graphical display of Gparted.  Instead of clicking there, click on the line that shows sda2 in the text portion below the graphics.  That will ensure that you have the right partition selected.

---

