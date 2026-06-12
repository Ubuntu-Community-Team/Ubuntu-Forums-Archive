---
title: "Fixing Partitions"
date: 2010-09-27
forum: General Help
---

### Post by Delsos on 2010-09-27
Sorry for the second thread but i had another question, i screwed up my computer before because when i first installed Ubuntu, i installed it as a partition, and then later i went to windows disk management and deleted the partition, and i guess that screwed up the MBR ..... so what is the proper way to remove ubuntu? i read a article, and it said to first fix the mbr, well i am not sure how to do that with windows 7....and then say i fixed the mbr, i would then go to delete the ubuntu partition from disk management? and after that the space becomes unallocated space....so how do i make it all one partition again?
 
thanks

---

### Post by spiky001 on 2010-09-27
ok lets get windows back 1st, you need the windows disc then when you boot off of it it will say something about repairing of fixing.     How did you install ubuntu dual boot or installed inside windows?  How do you want to install it this time?

---

### Post by AndThenWhat on 2010-09-27
I have also fixed this before using the Windows CD.  I think there's an option on the CD to fix your install and that will restore the MBR.

---

### Post by spiky001 on 2010-09-27
Have a read here [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Delsos on 2010-09-27
ok i fixed the MBR, now i will delete the ubuntu partition? and how will i make it all one partition?

---

### Post by spiky001 on 2010-09-27
Do yo want to dual boot?

---

### Post by Delsos on 2010-09-27
no i want to delete ubuntu, i deleted ubuntu from disk management, and now it is unallocated space, and i formated it, but now its a seperate partition, how do i make it all 1 partition again?

---

### Post by spiky001 on 2010-09-27
so you have windows on 1 partition and another partition which is unallocated space ( old Ubuntu ), if that is so when you get to the section on where to install put it in the unallocated space, that will give you 1st partition Win 2nd partition ubuntu

---

### Post by Mark Phelps on 2010-09-27
> **Delsos said:**
> no i want to delete ubuntu, i deleted ubuntu from disk management, and now it is unallocated space, and i formated it, but now its a seperate partition, how do i make it all 1 partition again?

You can't actually merge partitions. But you can expand an existing partition to fill the space.

Have you tried removing that partition and using Win7 Disk Management utility to expand the Win7 partition to fill the space?

---

