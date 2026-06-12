---
title: "Mirroring an active filesystem"
date: 2010-04-13
forum: General Help
---

### Post by TheSqueak on 2010-04-13
A couple of days ago, I noticed that palimpsest was reporting that one of my disks might be on the verge of failure. I had 3 500Gb disks in my system, and they were all reasonably full. Unfortunately, the disk reporting a possible failure is the one which contains both my / and /home partitions.

I have just installed a couple of 1.5Tb disks into the system, and set them up as a brand new mirror. I'm in the process of copying all of my media files across from their various partitions onto this new mirror.

Once this is done, I will be able to make enough space on one of the unfailing 500Gb disks to migrate my / and /home to.

I'm wondering how I can migrate these two filesystems with the minimum of disruption. Can I create a new software RAID mirror with a live filesystem as one side and have it sync up while I continue to work?

---

