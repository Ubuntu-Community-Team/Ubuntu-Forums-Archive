---
title: "Partition Help"
date: 2010-08-07
forum: General Help
---

### Post by joshklewis on 2010-08-07
I currently run a dual boot with Windows Vista and Ubuntu Lucid. I have been using Ubuntu for quite a while now, but kept around Windows "just in case." I have decided that keeping Windows is unnecessary and my Ubuntu partition is running out of space. I was wondering how I could format the Windows partition and add that space to the Ubuntu partition without having to format my entire computer.

---

### Post by TeoBigusGeekus on 2010-08-07
Boot up with a live cd, open partition manager (gparted) and grow your partitions as required.

---

### Post by Rubi1200 on 2010-08-07
Don't forget to right-click on the swap partition and choose Swapoff before proceeding with any other operations.
 
If you are unsure about anything post a screenshot of the partitions in GParted so we can take a look.
 
Most important of all, please backup any important files etc. before you start. With partitioning operations there is always a chance that things could go wrong.

---

