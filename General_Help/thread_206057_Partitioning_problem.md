---
title: "Partitioning problem"
date: 2006-06-29
forum: General Help
---

### Post by [h2o] on 2006-06-29
Hi!

After running Dapper Beta for a while, and having som trouble, I changed to SUSE. But now I am missing Ubuntu and was thinking of installing Ubuntu side-by-side with SUSE (and WinXP).

So, I booted the live CD and began the installation. Got to the partitioning and successfully resized my (oversized) NTFS partition to make room for Ubuntu, but then problems began. I had lots of space on the disk, but not enough partitions. My partition table currently looks like this:

hda1  WinXP
hda2  SUSE root
hda4  SUSE home
hda3  extended partition
--- hda5 swap

The partitioner wanted me to "create an extended partition" but there is already one. And I could not resize it.

Any suggestions on what to do? Removing any of the partitions is currently out of the questions since I don't want to trade away a working environment to a "maybe working".

---

### Post by Arisna on 2006-06-29
As you may know, you cannot create more than four primary partitions on an IDE hard drive.  That is the purpose of extended partitions, which do count toward your tally of primary partitions.  Extended partitions, however, can hold a number of logical partitions within themselves.

In your setup, you have hda3 set as an extended partition, and hda5 is a logical partition inside of it. You should be able to add logical partitions for Ubuntu under that extended partition.  Also note that you can use the same partition for /home under both installations, which will allow you to work with the same personal files on both if you wish, and that you can use the same partition for swap on both, since only one will be booted at any given time.

---

### Post by [h2o] on 2006-06-29
Yep,I know about the rules of partitioning and thus I wanted to resize my extended partition and add a logical partition inside it. But, the partitioning tool in the installer refuse to let me resize my extended partition, or add another logical partition inside it. I tried running the partitioning tool that comes with the Live CD as well (which was the same program, with a few more features) but no luck.

Any ideas?

---

### Post by Arisna on 2006-06-29
Would you be able to post a screenshot of your partitioner window?  I'm thinking the part you cut off the end of the XP partition has created empty space where it doesn't help you, and that you might have to move a whole bunch of stuff around to get this working. :(

---

### Post by [h2o] on 2006-06-29
Screenshot might take a while, but I think I remember what it lloked like.

> 
|-----------------------------------------------------------------------------------------------------------------------------------|
|                |                      |                                          |                               |                 |
| NTFS       |   Unallocated |   SUSE root                       | Suse Home            | extended  |
|                |                      |                                          |                               |  with swap |
-------------------------------------------------------------------------------------------------------------------------------------

Please excuse the crappy ASCII art, it doesn'tseem to like lots of spaces :)

---

### Post by Rui Pais on 2006-06-29
hi, 
whats the sizes of that partitions? and whats the size of empty space?

---

### Post by [h2o] on 2006-07-02
After the failure I restored my NTFS partition to its original size. 
But when I tried installing Ubuntu I freed 12 GB.

---

### Post by Rui Pais on 2006-07-02
So, you well you got

| NTFS | Unallocated (12G) | SUSE root | Suse home | extended [ swap ]|

but what are the sizes and free spaces of _**each**_ partition? (NTFS not needed) 
Until you give that there little suggestions that can be made... 

You know you can boot from a liveCD start gparted and do a screenshot with gnome-screenshot?

Under Linux, partition tools are quite good, but usually move partitions is not much implemented or is impossible in same cases, so if you didn't want to destroy things you may have to copy things around...

Please, post a screenshot or at least the sizes of Suse partitions and  they free space. An alternative would be mount those partitions and do a df -h command and copy+past the output.

---

