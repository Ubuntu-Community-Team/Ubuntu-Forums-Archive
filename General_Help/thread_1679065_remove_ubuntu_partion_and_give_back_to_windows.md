---
title: "remove ubuntu partion and give back to windows"
date: 2011-01-31
forum: General Help
---

### Post by yamaha83 on 2011-01-31
im sorry, im sure this has been asked before but my search didnt bring anything back except stuff from 2007 and i know the install is diffrent for 10.10 so figured removing would be diffrent as well. but im wanting to remove ubuntu and give back the partition to windows. i love ubuntu but i am a photographer and find myself in windows to use photoshop and the many plugins i have so much that at this point i would rather just have the extra space back for windows. any help is would be awesome! and once i get a new desktop for photo work my laptop will be back on ubuntu! :p

---

### Post by [Snc] on 2011-01-31
> **yamaha83 said:**
> im sorry, im sure this has been asked before but my search didnt bring anything back except stuff from 2007 and i know the install is diffrent for 10.10 so figured removing would be diffrent as well. but im wanting to remove ubuntu and give back the partition to windows. i love ubuntu but i am a photographer and find myself in windows to use photoshop and the many plugins i have so much that at this point i would rather just have the extra space back for windows. any help is would be awesome! and once i get a new desktop for photo work my laptop will be back on ubuntu! :p

Well in windows go to disk management, select the Ubuntu partiton(s), select something like clear or delete and then resize the windows partition.

more info here: [http://www.theeldergeek.com/hard_drives_05.htm](http://www.theeldergeek.com/hard_drives_05.htm)

ps. make sure, to do it in windows(!) this way, you will know, **not to delete** "c:" ;) and probably, windows "sees" an Ubuntu partition as "unallocated space", so one step less for you.

---

### Post by dhysk on 2011-01-31
For me when I did this with a vista machine, I had to repartition my linux partition to ntfs before the windows disk utility would see it for some reason. Anyway once I did that I could use the windows partition tool to take back the space.  So if Windows doesn't see it that would be my next step.  If the windows partition tool sees it than just reformat it to ntfs with that and off you go.

What I should have done is just leave it as it's own partition because I was back to Ubuntu sooner than I thought and had to repartition it again ;0....

If you are still using XP you will have to use Linux to reformat the drive since XP doesn't have a partition tool and wont see non windows formats.

---

### Post by yamaha83 on 2011-01-31
> **dhysk said:**
> For me when I did this with a vista machine, I had to repartition my linux partition to ntfs before the windows disk utility would see it for some reason. Anyway once I did that I could use the windows partition tool to take back the space. So if Windows doesn't see it that would be my next step. If the windows partition tool sees it than just reformat it to ntfs with that and off you go.
 
What I should have done is just leave it as it's own partition because I was back to Ubuntu sooner than I thought and had to repartition it again ;0....
 
If you are still using XP you will have to use Linux to reformat the drive since XP doesn't have a partition tool and wont see non windows formats.
 
currenlty on wondows 7 so ill give the stnadard tool a try and if that wont work i will use ubuntu to rest the partions to ntfs!

---

### Post by yamaha83 on 2011-02-09
ok so just not trying to do this and i see 2 unallocated partitions and i assume they are both for ubuntu? i gave ubuntu 50gig and i partition is 44.86gig and the other is 1.96... by question is do i just delete the 2 partitions? and not sure how to give the space back once i delete... and then last... i thought i read something about having to repair windows since i will be deleteing the ubuntu start up screen where i choose ubuntu or windows? is this true? cuz i dont have a windows cd or anything like that to do the repair if so??

---

### Post by Mark Phelps on 2011-02-09
Since you're running Win7, BEFORE you do anything else, use the Win7 Backup feature to create and burn an Win7 Repair CD.

You will need that later if your MBR got overwritten when you installed Ubuntu and you need to restore it to the original Win7 MBR.

---

