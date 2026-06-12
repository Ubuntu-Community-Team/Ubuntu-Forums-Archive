---
title: "SystemRescue Cd"
date: 2011-02-21
forum: General Help
---

### Post by COMPUTIAC on 2011-02-21
Hello, I would like to do a system back-up using this program. How long, on average should I expect this to take to accomplish , start to finish .          Several hours ?   

Is there any prep work to do or just let it fly ?

COMPUTIAC

---

### Post by seawolf167 on 2011-02-21
It depends on how large the drive is that you are backing up (i.e. 10GB partition will backup much faster than a 500GB full partition).

I personally do not use SystemRescue CD, but prefer [CloneZilla ]("http://www.clonezilla.org/")for backups. You can image any hard drive/OS. Store the images on an external hdd, backup the entire disk or just individual partitions, etc. Very highly recommend. My experience is that it generally backs up at ~.5-3 GB/min depending on system factors.

---

### Post by Mark Phelps on 2011-02-22
+1 for CloneZilla.

Backing up full install of Ubuntu 10.10 takes under 10 minutes.

However, I keep all my large data files on a shared NTFS partition and do NOT include that in the CloneZilla backup.

So, if you have lots of data, that will take a lot longer to back up.

---

