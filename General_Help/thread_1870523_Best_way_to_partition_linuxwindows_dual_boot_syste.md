---
title: "Best way to partition linux/windows dual boot system?"
date: 2011-10-27
forum: General Help
---

### Post by super_nerd on 2011-10-27
Hello,

I have been dual booting Windows XP and Ubuntu for a few years now and mainly use Ubuntu. However, the way I have this set up is less than ideal. I have a 250 GB Hard drive which has a Windows Partition, Linux partition and swap partition. On top of that I have been using a separate 500 GB Drive(actually two 500 GB with raid-mirroring) for data that uses a lot of space like movies, photos etc, and for stuff I want to share between windows and linux.

Now though, I want to have my linux system split into more partitions, so I can have separate /home and /usr partitions as well as a partition to share data between linux and windows. I was wondering what the best way to set up the partitions would be.

Also, I was wondering if it is possible and ok to make the /home partition the same one as the partition for shared data by using FS-Drive and moving the windows my documents path to this shared partition (something like /home/Windows/My Documents) so I don't have to manually add data to the shared partition. All my personal data would just be put there automatically by both OSs.

So I was thinking of doing something kind of like this:

250 GB Drive
--------------

Primary - Windows C:/ - NTFS
Primary - Linux / - ext3
Primary - Linux /boot -ext3

Extended
Logical - Linux SWAP - Linux SWAP
Logical - Linux /tmp - ext3
Logical - Linux /var - ext3
Logical - Linux /usr - ext3

500 GB Drive
-------------
Primary - Linux SWAP - Linux SWAP
Primary - Windows Paging - NTFS

Extended
Logical - Linux /home - ext3

But I have very little experience with partitioning so I don't know if this is a good idea or how much space to allocate to each partition. Anyone have any advice or information?

---

### Post by wolfen69 on 2011-10-27
If you have very little experience partitioning, what would be the benefit of you having 6 partitions for 1 linux install? Secondly, you can not put My Documents on a linux partition and expect windows to see/use it. 

My advice would be to have 1 partition for windows, another for common storage (ntfs), and 3 for linux. (/, home, and swap)

Unnecessarily adding partitions will not make your install run better.

---

### Post by 2F4U on 2011-10-27
Such a setup would make sense if you could distribute the partitions over more than one physical hard disk. In your case, I see absolutely no benefit in partitioning the system like you suggest.

---

### Post by oldfred on 2011-10-27
+1 on wolfen69 suggestions.

Herman has more info on why or why not separate partitions. Really only for a server and then you want to know usage patterns.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

I usually suggest a separate /home for new users, but once you get to having one or more data partitions it is better just to leave /home inside / (root) and mount the data partitions into /home so it looks like the data is in /home. I use links which works for Ubuntu but may have issues if also booting other non-Debian distributions or connecting with Samba.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below. I also prefer for reliability to have entire bootable system on each drive and link to data on other drives. Then if one drive fails I can still boot. If system is on multiple drives all drives have to keep working.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)


Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
I use this logic but I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

