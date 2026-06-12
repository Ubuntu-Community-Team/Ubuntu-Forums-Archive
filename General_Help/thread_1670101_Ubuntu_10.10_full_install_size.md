---
title: "Ubuntu 10.10 full install size?"
date: 2011-01-18
forum: General Help
---

### Post by maxppp on 2011-01-18
Hi guys, am planning to install ubuntu 10.10 on an ssd disk drive, but it only has an 8gb capacity (dell mini 910).

1 - What is the default size of a full install of 10.10?
2 - Is it best to let the partition manager auto configure the drive partitions and formats?

---

### Post by 3Miro on 2011-01-18
A default install is about 1GB. The requirement is that you have at least 2GB so you can run comfortably. 8GB is plenty (so long as you don't install too much additional software).

Check on the situation of swap space and SSD (I don't know if there are any issues).

On a drive as small as 8GB, I wouldn't use the "default" partitioning. I would just give it all to Ubuntu as / (root), however, check on possibly needing a swap partition.

---

### Post by lithopsian on 2011-01-18
It will fit, no problem there.  You will even have a good amount of space left over for more applications.

However I should point out that you are increasing the risk of running out of space when a log file goes mad, or your trash doesn't get emptied for a while.   You could easily fill your disk with a few icon themes and a couple of games.  I really hope you have other storage options available.  For example, mounting /home and a swap partition elsewhere, perhaps also moving /var elsewhere, would be a very good idea.

If the 8gb is all you have, then just have a single partition and use a small swap file (not a partition).  See how it goes, if you need more swap you can add another swap file or increase the size of the one you have.  You won't be able to hibernate and you won't be able to download much, but you will be able to browse the net and use email.

---

### Post by ajgreeny on 2011-01-18
1.  About 2.6GB before you add any other applications or your own data files for a standard desktop system.

2.  With such a small size disk it is not feasible to consider a separate /home partition, so I think it is definitely best to allow the system to set partition sizes as default.

The one thing I am not too sure about is the file-system best for formatting a SSD install.  I know that for a standard flash drive it is thought best to use ext2 so as to limit the number of writes to disk; I don't think the same is true of an SSD, but it is worth looking into a bit more before deciding which format type to use.

EDIT:
@3Miro:  Are you sure you can get Ubuntu into just 1GB?  My newly installed root partition not including my home, which is in a separate partition, is always around 2.6GB.  I always use a clean install, so it is not a result of old archived packages or anything of that sort, so I am surprised to think you have managed to fit it into 1GB.

---

