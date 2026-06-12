---
title: "Recovering partition with TestDisk"
date: 2009-06-28
forum: General Help
---

### Post by Johanc on 2009-06-28
Hey

I accidentially deleted one of my partitions while installing the new version of Ubuntu. 

I am trying to recover the partition with TestDisk. I am following this guide: [http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformated_partition](http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformated_partition) 
where it says:

 [I][B] Recovery of reformated partition
[/B][/I]
[I]If the partition has been reformated to another filesystem (FAT32 formated as NTFS or vice-versa),

    * run TestDisk,
    * select the harddisk, the partition type
    * choose Advanced
    * select the partition
    * choose Type,
    * enter the value corresponding to the previous filesystem
    * choose Boot
    * choose RebuildBS
    * List
    * If you can see your files, choose Write and confirm
    * In Analyse, choose to rewrite the partition with the correct partition type. [/I]

My problem is that when I get to the point where I should have the option *Boot* this option dosen't show up. I am left with the same options as before I chose *Type*... 
The options are: Type, Superblock, Image Creation and Quit. 
None of them seems to be able to recover my partition. 

Can anyone answer what I am doing wrong? (I am using the newest version 6.11). Am I maybe using the wrong guide??

please help...

---

### Post by blueridgedog on 2009-06-28
I think this thread has better steps:

[http://ubuntuforums.org/showthread.php?t=1147563](http://ubuntuforums.org/showthread.php?t=1147563)

---

### Post by drs305 on 2009-06-28
Johanc,

When I run testdisk, following the instructions you posted, I go to Advanced > Type > Proceed and then have to enter the number of the type of partition. When I enter a partition type that exists on the partition, I get the "Boot" option. 

When I enter a partition type number that *does not* exist on the partition I selected earlier, I *do not* get the Boot option. It's possible that the type of partition you are choosing does not exist on the partition or at least isn't being seen by Testdisk.

ADDED: If I select type Linux (83), it does not give me a "Boot" option. If I select a different type of format, the "Boot" option is displayed.

---

### Post by Johanc on 2009-06-28
The thread-post didn't help, I tried it but it didn't make any positive result. 

That is very strange, because it is/was a standard ext3-partition, and I (as well as the program) chose the 'Linux' option (83). 
By the way the new partition(-table) looks exactly like the old one- just now without the data. Could that make any difference?

---

### Post by Johanc on 2009-06-28
By the way Photorec can find my data and recover it, but it is so parted in small pieces that it is actually not a help. Just to say that the data can be found and recovered, just need to find a better way...

---

