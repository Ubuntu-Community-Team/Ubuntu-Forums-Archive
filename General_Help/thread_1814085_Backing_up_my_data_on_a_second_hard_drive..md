---
title: "Backing up my data on a second hard drive."
date: 2011-07-28
forum: General Help
---

### Post by MutantJohn on 2011-07-28
Hello All,

So, I recently acquired a second hard drive (1.5 TB) and I wish to partition Ubuntu 11.04 with Windows 7. I've set everything up properly and using the Disk Utility in my System Settings I've created a 1 TB partition which I want to use for Linux. I think it has the proper partition type but how do I exactly go about transferring all my files from the hard drive I'm using now to the partition I would like to have? Thanks in advance to any of those that so choose to reply.

---

### Post by Rodney9 on 2011-07-28
You could do it several ways, you could use [Clonezilla]("http://www.clonezilla.org/") or follow these [instructions]("http://ubuntuforums.org/showthread.php?t=35087"), thanks to Heliode

---

### Post by oldfred on 2011-07-28
Do you really want a 1TB partition for Linux? The entire system fits into 4GB and with lots of programs grows to 6 or 7GB. I regularly install into 20-26GB so I have lots of room. But then all my data is in other partitions. With a smaller system partition you do not have system files scattered all over drive but near each other for speed of loading. Then data that is accessed less frequently can be in the larger partition. 

Also if you have to run chkdsk or fsck a very large partition takes longer. If you ever have a hard disk failure and try to recover data it can take forever.

If storing lots of movies then you may want a very large partition.

Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

With two drives I prefer to have Windows on one drive and Ubuntu on the other.
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

