---
title: "Size of partitions on a win7 box"
date: 2010-11-22
forum: General Help
---

### Post by twojo6 on 2010-11-22
Hi, I have a new win7 pc with a 2TB harddrive.
Only a C drive exists, only win7 is on the pc.
I would like to triple partition for win7, ubuntu, and all other files-data, music, etc.
And I understand this can be easily be done via the disk management feature.
 
Obviously a 2TB HD is huge for me and I probably will never come close to filling it.
I will eventually copy all my files from my old pc, but that totals about only 10GB.
 
My issue is what should be the actual size of the win7 and the ubuntu partitions? 
How many GB for win7 and how many GB for ubuntu?
 
TIA for all replies.

---

### Post by jehiva on 2010-11-22
Just be careful you don't choose the "Use entire partition" option when installing Ubuntu or it will erase your Windows 7 partition as well.

---

### Post by Verbeck on 2010-11-22
the windows installation requires 15-20 gb
ubuntu needs 5-6 i think

*that's without user applications so it should actually be larger

---

### Post by twojo6 on 2010-11-22
"the windows installation requires 15-20 gb
ubuntu needs 5-6 i think"
 
ok, thanks
that's the minimums, I think
 
I am looking for recommendations of GB for each partition: win7 & ubuntu
 
my HD is 2TB! huge!
is 100GB for win7 and 100GB for ubuntu a good idea? 

is there a lessening of efficiency if I make them 100GB each?
if say only 20% of the 100Gb is used, for now, is that inefficient?
 
Trying to think logically here. Maybe I am giving it too much thought?

---

### Post by oldfred on 2010-11-22
Everyone has there own opinion on partitioning and none are really wrong. A lot depends on how you plan to use system. Will you be downloading a lot of data? If so large data partition(s). Are you thinking about installing other operating systems? Then perhaps a few extra / (root) partitions. Will you upgrade in place? Then a separate /home makes that a little easier. As time goes on and you use system your needs also change so sometimes leaving some unpartitioned space may make sense. Having partitions too large also makes windows chkdsk or Linux fsck take longer. And hopefully not required recovery of data can take forever with large partiitons. Partitions that are too small make it difficult to organize as you may want more space later. Its all trade offs.:)

Ubuntu does not require much space. I have installed many programs and have used about 6GB of my typical 25GB root partition. I move all data out of /home and /home is only about 1GB. Of course data can be huge depending on what you do. Normally Ubuntu's data is in /home whether /home is part of root or a separate partition. I do recommend a separate NTFS shared partition if dual booting with windows. I do not recommend directly writing into the windows partition if it can be avoided.

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up. Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM.

Use windows tools to shrink the win7 partition or create a NTFS partition for windows first and put a boot flag on it. Then you will only use one primary partition instead of two. Use gparted to create all the other partitions. Leave one primary available and put all the other partitions in an extended partition that is last on the drive. Then you can adjust easier.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by twojo6 on 2010-11-23
Thanks so much for the info. I will take the time and read it all before partitioning. And will come back here with any additional questions. Thanks again. Tom

---

