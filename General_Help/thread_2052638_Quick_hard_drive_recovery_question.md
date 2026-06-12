---
title: "Quick hard drive recovery question"
date: 2012-09-03
forum: General Help
---

### Post by Alcidious on 2012-09-03
Hey everyone,

I posted a few days ago about a problem I had while trying to back up my system.  Due to a system freeze caused by a particular kernel issue I am trying to debug (following directions from bug squad), the backup corrupted my file system b/c I had to shut off the computer.

While I am running Ubuntu 12.04 32-bit on a Samsung laptop (and also on a Desktop PC), the external hard drive filesystem is NTFS (The hard drive was originally set up under a windows operating system, and i was still using that file system even w my linux systems {still a dumb newbie}).

CoffeeCat told me to follow the instructions for hard-drive error retrieval/fix using a windows computer.  I am now running that process on my friends laptop, but he has to leave.  

WILL SUSPENDING THIS PROCESS, OR MY FRIENDS COMPUTER, CAUSE FURTHER DAMAGE TO MY FILES? WHAT SHOULD I DO? HE HAS TO LEAVE IN 15 MINUTES!???

Thanks!

---

### Post by Mark Phelps on 2012-09-03
Since the 15 minutes is long gone, maybe it doesn't matter now ... but if you want help with a windows "process", you should at least tell us the name of the app you're running.  Saying "process" doesn't tell us anything useful.

Anyway, in general, a recovery app works best if you let it run until it has examined the entire file system on a device.  Stopping it part-way through, unless you are looking for a specific file and have already found it, compromises the chance of recovering files.

---

### Post by Alcidious on 2012-09-04
Thanks Mark, 

I was freaking out about potentially losing my entire life's academic and artistic writings! My friend was good enough to keep his computer running, with my ex-HDD attached to it, all the way home and all my data was recovered.  

Although I am becoming a stronger linux user, I should have known better than to keep using an NTFS file system.  What should I do now to reformat the ex-HDD and save all that info back on to it?  Is there a way to reformat without moving the data off of the disk and then back on to it? Any recommended resources you could refer me to?  Thanks a lot, and next time I will try to not freak out and be more thorough in my descriptions!

---

### Post by Mark Phelps on 2012-09-04
For "casual" storage, especially in the situations where you need to share data between Linux and MS Windows systems, NTFS is an OK filesystem to use.  Problem is, though, if the filesystem gets corrupted, you nearly always have to use MS Windows utilities to repair it.

If you're not going to share data anymore, then formatting to Ext4 would be the better way to go -- as Linux utilities will then be able to do data recovery on that filesystem.

---

### Post by Alcidious on 2012-09-04
ill be going w Ext4... I really despise microsoft.  Thanks a lot!

---

