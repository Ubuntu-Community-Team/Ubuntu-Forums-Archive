---
title: "Is this an ok HDD Partition Setup for triple boot?"
date: 2010-11-01
forum: General Help
---

### Post by Saulace on 2010-11-01
Hello, I've looked everywhere for a satisfactory answer, to no avail. :(
I wish to triple boot xp/98/ubuntu 10.10. 
Is this an appropriate HDD setup? (it looks like this in partition magic pro srever 8.05)
 
*:SYSTEM........ NTFS......... primary ..........(for xp)
C:WIN98......... fat32 .........primary,active (for win98 )
*:UBUNTU....... LinuxExt3 ...Primary ..........(for Maverick Meerkat)
.........* Extended 
............. *:SWAPSPACE2.... Linux swap .....logical
. ...........D: DATA................. fat32............. logical (for all things backup)
 
There is nothing on any of the drives at this point. (I am submitting this on a crappy 233mhz win95 laptop)
 
Here's the information i've gathered so far...
Install in the following order: 98, XP, Ubuntu
XP's drive label MUST be "SYSTEM" (I think?)
Installing multiple os's is easy (i've read) if you hide unused partitions during install (ie. if installing XP, hide C:WIN98 and *:UBUNTU partitions) but i can only do this with FAT formats, and if i do that, the dirve letter changes, which is a problem (i suppose i could manually hide/unhide, and set active the partition I want at every boot-up....(Damn))
 
And here's a couple more questions
SHOULD I make everything fat32?
do they have to be primary to boot? ('98 on an inactive partition won't load)
Once they are all installed... where do i put grub? Do i put it in first?
Also, I deleted my dell utility partition to do this, is that a problem? (LOL, I have NO idea what I'm doing...Fck)
 
Like i said, finding information about the partition setup (logical/primary) is damn near impossible. So thanks in advance for whatever you can help with.:P Even if it's just a "Ya that'll do for a setup"
 
I'm gonna keep experimenting, since there's no longer anything to lose on my HDD, and i'll report back any improvements I come across

---

### Post by oldfred on 2010-11-01
Not sure about '98.

Windows needs to be on primary partitions and the boot flag is what sets the active partition. NTFS is better than FAT, both XP & your shared data should be NTFS. Does not win98 have to be FAT? Ubuntu will not work in any MS formats, it uses linux formats ext3 or ext4 (plus many others). Unless you are doing a wubi install?

I do not know if this works the same for win98 and XP.
To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

You can also use gparted which is on the Ubuntu liveCD to create & modify partitions.
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

---

### Post by Saulace on 2010-11-05
I was hoping to know if that setup was right, however those resourses are awesome, so thank you

---

### Post by oldfred on 2010-11-05
Your partitions will work. I just do not recommend FAT anymore for any large partitions. NTFS is better but I do not know anymore if win98 will work with NTFS.

I also like to have a NTFS shared partition so from linux you do not have to write into the windows system partition. You can read from the windows system partitions without problem.

I also like to have /home as a separate partition.

But your will work. I find every few years I find I want to reorganize based on how I use system, and then I find I have to buy a new drive as I have filled the old ones anyway.

---

### Post by Saulace on 2010-11-05
That's funny about the new hard drives, I've heard the best thing to do is swap out drives... On the other hand, WINE has just obliterated all my needs for windows, so thanks for the help guys, but I'm good to go...  Now all i have to do is merge the other primary partitions with this one so i have more space for stuff.  I'm pretty sure that's somewhere in these forums.

---

### Post by oldfred on 2010-11-05
I do not like moving partitions left. Somewhat higher risk. Make sure you have good backups which you should have for any system changes. You could just make the partition a data partition and mount or link it into your root.

---

### Post by e24ohm on 2010-11-06
> **oldfred said:**
> Your partitions will work. I just do not recommend FAT anymore for any large partitions. NTFS is better but I do not know anymore if win98 will work with NTFS.

I also like to have a NTFS shared partition so from linux you do not have to write into the windows system partition. You can read from the windows system partitions without problem.

I also like to have /home as a separate partition.

But your will work. I find every few years I find I want to reorganize based on how I use system, and then I find I have to buy a new drive as I have filled the old ones anyway.

Is it possible to Read and Write safley now to NTFS partitions? I thought NTFS was still a big "no-no"; however, I am coming from Red Hat/Fedora.

---

### Post by oldfred on 2010-11-06
About 4 years ago I used FAT32 as a shared partition with XP and Ubuntu as then they said the NTFS was not quite ready yet. 

About a year ago I was losing data in my FAT32 partition as it does not let files be larger than 4GB (less one byte). I converted to NTFS and it is considered very good. That said I do not write into a windows system partition. I share data in a common data partition and only read from the windows system partition unless I have to make repairs from Ubuntu.

Those that have issue often do not run chkdsk regularly, hibernate windows & then write into the system partition corrupting the hibernation, or accidentally moving some system files in windows and corrupting it. The NTFS drive does not hide files like windows and lets you do anything which can be risky. I avoid it just so I do not make an error.

---

### Post by e24ohm on 2010-11-08
> **oldfred said:**
> About 4 years ago I used FAT32 as a shared partition with XP and Ubuntu as then they said the NTFS was not quite ready yet. 

About a year ago I was losing data in my FAT32 partition as it does not let files be larger than 4GB (less one byte). I converted to NTFS and it is considered very good. That said I do not write into a windows system partition. I share data in a common data partition and only read from the windows system partition unless I have to make repairs from Ubuntu.

Those that have issue often do not run chkdsk regularly, hibernate windows & then write into the system partition corrupting the hibernation, or accidentally moving some system files in windows and corrupting it. The NTFS drive does not hide files like windows and lets you do anything which can be risky. I avoid it just so I do not make an error.

so you are saying - that you have had good experiences with having a ntfs partition, which is only used as a data share? I didn't know NTFS was OK to use yet. Thanks for telling me.

Sorry - we can get the thread back on track. Thanks.

---

