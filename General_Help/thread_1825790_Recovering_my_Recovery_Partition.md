---
title: "Recovering my Recovery Partition"
date: 2011-08-15
forum: General Help
---

### Post by T3rminus on 2011-08-15
Ok so I have done a lot of stupid things in my life but this has to be one of the worst screw ups of all time. Out of all of the many MANY problems I have had, and continue to have with Ubuntu, this is the worst. I am getting better at trouble shooting with Ubu and all but I need some help with this one.

   When I was installing Ubuntu I think that I might have deleted all of the other partitions on my 500GHD including my Recovery. I really REALLY what to return to factory settings but I cant figure out how to fix this issue. I am currently running scans with TestDisk partition recovery but I don't know if it will find anything. Is there any other possible way to get my Recovery partition back? 

Thx

Post Scriptum : I am running an HP Pavilion dv6-3122us Entertainment Notebook.

---

### Post by Jerry N on 2011-08-15
Didn't you make a recovery DVD set when prompted during your computer setup?  You might be able to buy a recovery disk set from HP.  The last time I did that for someone the cost was about $15.

Jerry

---

### Post by Actonix on 2011-08-15
If you have only just deleted the partition and NOT gone ahead with the Ubuntu install among other things you might have a chance at recovering the partition in place.

First things first, you do not want to do anything that might make any changes to what's on the hard-disk, that includes running any applications installed on that hard drive - Whatever recovery tools you run should be run from external media ie a CD-Rom drive or another Hard disk installed as Master.

It would also help if you were aware of the relative size of all the partitions that existed prior to deletion, the most important of these obviously being the size of the recovery partition - whatever software you use should hopefully be able to query the MBR and Fat tables for the partition in question as well as do an in-place restoration of the partition - after the recovery you probably also need to ensure the partition type is correct - most likely a type 12 Hidden

---

### Post by Mark Phelps on 2011-08-16
> **T3rminus said:**
> Is there any other possible way to get my Recovery partition back? 

The problem with using Linux file recovery tools is that, all to often, they can't recover the original MS Windows filenames.

If you can hook up your drive to a Windows PC, then do the following:
1) Download and install the trial version of GetDataBack for NTFS from Runtime Software
2) Run the app in deepest discovery mode -- best to run overnight
3) Check in the morning to see if it found your Recovery partition
4) You will have to purchase it to do the actual recovery -- but at least you can try it out for free.

---

