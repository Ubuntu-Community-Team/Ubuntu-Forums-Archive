---
title: "Gparted problem (re) partitioning hard disk"
date: 2011-10-23
forum: General Help
---

### Post by Finn bjerke on 2011-10-23
I have Dual boot Ubuntu 10.10 and 11.10 on same harddrive. 2 partitions also some swapfile partitions I guess. I now need to allocate more harddrive space to the Ubuntu 11.10 partition. I want to reduce the size of the Ubuntu 10.10 partition and expand partition with 11.10 

1. I have used CD live and booted form it. Gparted is on that CD. I run it form terminal using roots rights. 
2 I resized the partition with Ubuntu 10.10 from the CD Gparted function making it smaller, from that operation I now have 60 gigabyt unallocated extra diskspace.:)
3. Now I want that extra space allocate d to partition where I have Ubuntu 11.10. I cant do it for some reason.

Maybe its easier to understand if you look at the screen dumps


[IMG]http://gratisupload.dk/billede/thumb/667731/[/IMG]

Better view here.
[http://gratisupload.dk/vis/667731/](http://gratisupload.dk/vis/667731/)
bigger image here:
[http://gratisupload.dk/vis_billede/667731/](http://gratisupload.dk/vis_billede/667731/)

help greatly appreciated, I need to merge the unallocated diskspace into the /dev6 you can it on the right

---

### Post by conradin on 2011-10-23
Those images dont view well onmy computer for some reason, but Ill assume sda6 is the small full looking partition on the far left. Is sda6 the boot partition? (just currious, doesnt really matter, unless things get screwed up.)

So i think you can only allocate free space to something part of the same extended partition (if Im wrong, someone please correct me).

So What you would need to do is create an image of /dev/sda6 and save it some place as an image file. dd works well for that as does dd_rescue.

Then delete sda6, and merege the free space and create a partition for sda6. Then, you have to restore the sda6 image file to the new partition, where you will then have a sectionof free space that you can re-allocate using gparted to sda6.

---

### Post by Finn bjerke on 2011-10-23
Sorry the photo is not visible for you. Myabe its easier if you click the links under the photo. You can download the photo on the yellow bar under the small version of it. scroll down a wee bit and there you have it. 

I have one harddrive and several partitions. 

1. sda6 is my ubuntu 11.10 boot partition, Id like to make that disc bigger. 
2. sda1 is my ubuntu 1o.10 bootable partiotion disk, I have repartitioned that and I now have dual boot using 2 ubuntus.
3. There are smaller swapdisks too.

Im n ot sure I understand this sentence: 

*```
something part of the same extended partition
```*

I need more info about primary and extended partition I guess??

---

### Post by oldfred on 2011-10-23
You can move /home to its own partition or if sharing with two Ubuntus create a shared /data partition. I generally recommend / (root) partitions be only 10-20GB when you have a separate /home or all your data is in /data.

You can do what you want but have to include the unallocated in the extended partition. If you move the extended partition left then the unallocated will be in the extended. Then you can move sda6 left, but it may take a long time. It should not change /dev/sda6 or UUID but have a liveCD available to reinstall grub2's boot loader just incase.

The extended partition is one primary partition that is a container for all the logicals, but you still have to treat the extended as a primary partition.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

---

### Post by tredsyn on 2011-10-23
If you want to put the unallocated space to the largest partition you need to "resize" [dev/sda2], making it bigger. The unallocated space will now be inside [dev/sda2]. After that you can now "resize" [dev/sda6]. BTW I noticed you have 2 swap partitions, one is 11.72 GiB. You just need one. For the size of the swap partition, usually it's 2x your RAM.

---

### Post by Finn bjerke on 2011-10-24
This is a very good solution you are suggesting. 

2 small Ubuntu partitions with the programmes and one big data disc.

---

### Post by oldfred on 2011-10-24
Since I bought my new "large" HD a couple of years ago (640GB is now not so large), I have made new 25GB root partitions for every install plus a few for testing different things. I then have two data partitions one is NTFS for sharing with my old XP which I now rarely use and the other ext3.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

