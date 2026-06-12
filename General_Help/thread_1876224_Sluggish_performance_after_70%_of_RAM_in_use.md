---
title: "Sluggish performance after 70% of RAM in use"
date: 2011-11-05
forum: General Help
---

### Post by abeep on 2011-11-05
Hi, I am using  ubuntu 10.10 (2.6.35-30-generic, also tried 2.6.36-020636-generic) on my lenovo-410 64-bit laptop,  having 8gb of ram. the system works absolutely fine, the performance is  good, but when the memory reaches to around 5gb then the system  performance is sluggish, I know Its basically because of the paging of memory which is causing this,
 i had set **cat /proc/sys/vm/swappiness**  to 0 . so i tried to  disable swapping by setting swapoff, in this case it did not write paged  memory to swap file but the result was even worse, i.e. when 5gb memory  was used the system just got stuck, and the HDisk light was  continuously blinking. 
So is there any setting which could resolve the issue and avoid paging,  as my laptop has ample amount of RAM. It would be of great help if  someone has solution for the same

---

### Post by dcstar on 2011-11-06
> **abeep said:**
> Hi, I am using  ubuntu 10.10 (2.6.35-30-generic, also tried 2.6.36-020636-generic) on my lenovo-410 64-bit laptop,  having 8gb of ram. the system works absolutely fine, the performance is  good, but when the memory reaches to around 5gb then the system  performance is sluggish, I know Its basically because of the paging of memory which is causing this,
 i had set **cat /proc/sys/vm/swappiness**  to 0 . so i tried to  disable swapping by setting swapoff, in this case it did not write paged  memory to swap file but the result was even worse, i.e. when 5gb memory  was used the system just got stuck, and the HDisk light was  continuously blinking. 
So is there any setting which could resolve the issue and avoid paging,  as my laptop has ample amount of RAM. It would be of great help if  someone has solution for the same
Post this:
```
uname -a
```

---

### Post by abeep on 2011-11-06
Linux apatil-T410 2.6.35-30-generic #61-Ubuntu SMP Tue Oct 11 17:52:57 UTC 2011 x86_64 GNU/Linux

---

### Post by dcstar on 2011-11-07
RAM is probably not the issue, other processes hammering the disk are.

What do you have running that uses 5GB of RAM?, there is only so much a laptop can handle.

---

