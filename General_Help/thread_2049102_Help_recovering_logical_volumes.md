---
title: "Help recovering logical volumes"
date: 2012-08-27
forum: General Help
---

### Post by PHS Philip on 2012-08-27
I had a single 2TB disk LVMed into 5 partitions (var, tmp, swap, and 2 data partitions). I was adding 2 more 2TB disks which I was planning to set up as a degraded RAID 5 array, then migrate my LVMed stuff to there, then add the old disk to the array. But, I wasn't careful and didn't check what disk I was working on, so I wrote mdadm metadata over the LVM metadata.

I realized this pretty quickly (ie before setting anything up), so I tried to recover the LVMs. I was able to do reasonably well, initially. I had all of them recognized by LVM (although the last one gave errors when I tried to get device-mapper to see it). However, they can't mount, fsck can't find their superblocks, and neither can dumpe2fs. 

BUT! When I cat | less the partitions from /dev/mapper, I can see all my data and things that look (to my relatively ignorant eye) like superblocks. Is there anything I can do to get these recovered, either from those blocks or by extracting my data?

Thanks in advance :)

---

