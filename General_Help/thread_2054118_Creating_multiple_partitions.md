---
title: "Creating multiple partitions"
date: 2012-09-06
forum: General Help
---

### Post by matimont on 2012-09-06
Hi,

I have a partition I'm not using, see below:


Disk /dev/vdb: 21.5 GB, 21474836480 bytes
3 heads, 34 sectors/track, 411206 cylinders, total 41943040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29a10d7f

   Device Boot      Start         End      Blocks   Id  System
/dev/vdb1            2048    41943039    20970496   83  Linux


I would like to create partitions of 1GB let's say to be mounted under /home/user/public_html/directoy.

How can I create 20 partitions of 1GB? does it makes sense to do so to provide a user with more disk capacity? Basically I host websites and since each user has different storage needs, I'd like to address each one individually by increasing their folder according to their needs, so for example user1 wants to store videos on a folder, then I can mount a 1GB partition under /videos, am I making sense?

Thank you

---

