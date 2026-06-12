---
title: "Help with Ubuntu Installation ASAP!!"
date: 2011-12-16
forum: General Help
---

### Post by jrozo17 on 2011-12-16
I am trying to partition my hard drive and I want to keep Windows on it. I am trying to partition it to install Ubuntu along with Windows.

Here is what it shows...


**Device   |    Type  |   Size   |    Used**

/dev/sda              
/dev/sda1 |   ntfs   |  104MB   |   60MB 
/dev/sda2 |   ntfs  |   627251MB |  unknown
/dev/sda4 |   ntfs   |  12775MB |   10780MB



Can someone tell me which one to choose? I dont want to end up deleting everything.

---

### Post by Derek Karpinski on 2011-12-16
Can you please boot into windows and take a screenshot of 'My computer' that shows all your drives.

I'm guessing that you have a 'recovery' partition, some weird boot partition Win 7 has, and the standard partition.

Post your screenshot here so we can help.

---

### Post by Docaltmed on 2011-12-16
Before repartitioning, always, always have a backup. That's step 1. You may have already done that, if so, please ignore this notice from the Public Backup Safety Commission.

---

### Post by Mark Phelps on 2011-12-16
You haven't provided enough detailed info for an accurate answer.

Open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the details of the partitions on your drive.

Once you post that back here, we can better advise you.

Also, open the Disk Management utility in Win7, look at the "drives" and see if there are already four of them (including a possibly hidden Recovery partition).  If there are, you will have to REMOVE one before you can continue.

---

