---
title: "Extend partition problem"
date: 2010-07-14
forum: General Help
---

### Post by PcFrk256 on 2010-07-14
I'm trying to extend my primary partition, but the unallocated space is all the way to the right. 

[IMG]http://t3xtual.com/PartitionIssue.jpg[/IMG]

How can I move the unallocated space over so I can extend it?

---

### Post by m4tic on 2010-07-14
I can't see the image mate
Boot from an Ubuntu live cd. Go to System->Administration->Gparted(or maybe its now called partition editor). 
From there everything is straight foward, just grab and slide the partition or do whatever you wish to. Be aware that it takes a long time to move partitions, if it's over 100Gb be prepared to wait hours my friend.
The first thing i do when partitioning an empty drive is to set an extended partition. From there i start from the left as it's easiest. Keep that in mind for next time

---

### Post by 3Miro on 2010-07-14
The only way would be to go partition one by one, extend it to the right and shrink it from the left. It will take many extend/shrink commands so: BACKUP ABSOLUTELY EVERYTHING THAT MAY BE IMPORTANT. With that many operations, it is very likely that something will go wrong.

Another possible way would be to "move" a partition, i.e. create a new partition in the unalocated space and then move all data from the partition immediately to the right of the one you want to extend. Then remove that now empty partition and you will be able to extend the main one (read the thing about backup).

Also, I am not sure it is possible to shrink a partition "from the left". Other than that, I see no other way. The partitions have to correspond to contiguous hardware blocks, so you cannot easily move them like you would move files.

If all else fails, you can always reformat and reinstall everything.

---

