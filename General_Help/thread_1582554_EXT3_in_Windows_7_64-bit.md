---
title: "EXT3 in Windows 7 64-bit"
date: 2010-09-26
forum: General Help
---

### Post by gnomeout on 2010-09-26
Hi,

I know there are a lot of forums on this topic and I have been scanning them periodically for months, but no one has been able to come up with a clear solution for this problem.

Here are the facts. I have successfully installed and configured ext2fsd as my driver on Windows 7 64-bit. Everything about the installation went fine and I chose this driver because the other popular choice has a lot of extra stuff about being limited to an inode size of 128. Which I believe I have a larger size than that, although I cant remember the last time I formatted my home folder partition, but it wasnt too long ago(maybe a year tops) and it is ext3. 


The installation appears to have worked and it sees that I have several ext partitions, and I have my home folder partition configured as a permanent mount point every time windows starts. But whenever I go to access this partition, windows tells me it needs to format the drive and it can't access it. 

This used to just have to do with a bad shutdown or something where the partition wasnt unmounted properly, but that does not seem to be the case anymore. I have run fsck from a live CD and cleanly unmounted my partition before booting windows, and still nothing. 

I had the same driver working perfectly not too long ago but I had to reinstall and now I get this nonsense. 

Help????

---

