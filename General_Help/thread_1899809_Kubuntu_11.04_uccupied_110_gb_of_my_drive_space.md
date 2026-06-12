---
title: "Kubuntu 11.04 uccupied 110 gb of my drive space"
date: 2011-12-24
forum: General Help
---

### Post by tehno 2 on 2011-12-24
Hi, can some one help me. I installed Kubuntu on a separate  120 GB partition from inside windows 7. now after the several updates, i fined that Kubuntu is taking about 110 GB which looks very strange to me and I am sure after some more updates, i am gonna run out of enough room to run it.

I need your help because I love Kubuntu and do not want to lose it.

---

### Post by nothingspecial on 2011-12-24
You may have a log that's being written to a lot. What does ```
du -h /var/log/*
```
say?

Is there anything huge in there?

---

### Post by Basher101 on 2011-12-24
If you did not make a manual installation then the Kubuntu installer has taken 10 GB for SWAP. You can see here what SWAP is for: > Linux divides its physical RAM (random access memory) into chucks of memory called pages. Swapping is the process whereby a page of memory is copied to the preconfigured space on the hard disk, called swap space, to free up that page of memory. The combined sizes of the physical memory and the swap space is the amount of virtual memory available.

Swapping is necessary for two important reasons. First, when the system requires more memory than is physically available, the kernel swaps out less used pages and gives memory to the current application (process) that needs the memory immediately. Second, a significant number of the pages used by an application during its startup phase may only be used for initialization and then never used again. The system can swap out those pages and free the memory for other applications or even for the disk cache.

However, swapping does have a downside. Compared to memory, disks are very slow. Memory speeds can be measured in nanoseconds, while disks are measured in milliseconds, so accessing the disk can be tens of thousands times slower than accessing physical memory. The more swapping that occurs, the slower your system will be. Sometimes excessive swapping or thrashing occurs where a page is swapped out and then very soon swapped in and then swapped out again and so on. In such situations the system is struggling to find free memory and keep applications running at the same time. In this case only adding more RAM will help.

Linux has two forms of swap space: the swap partition and the swap file. The swap partition is an independent section of the hard disk used solely for swapping; no other files can reside there. The swap file is a special file in the filesystem that resides amongst your system and data files. In your case you have only the swap partition.

---

### Post by tehno 2 on 2012-01-03
Well,
thank you guys, nothing worked out with me and after latest updates, I don't have a single bite left on the drive. I think I will have to uninstall Kubuntu, format drive and do new install.

---

