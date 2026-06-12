---
title: "Ubuntu version, installation &amp; tuning for SSD netbook?"
date: 2011-10-05
forum: General Help
---

### Post by MobileTechie on 2011-10-05
I'm currently running Ubuntu 9.04 NBR on an Asus 901 with a 32GB Runcore SSD added to the existing 4GB PHISON SSD. The Asus has 2GB RAM.
 
I installed it using ext4 file system on the runcore SSD and using the 4GB SSD as the swap partition.
 
Since then I've been reading suggestions that one should not use ext4 on an SSD because the journaling will wear the SSD out too fast but then others say that doesn't apply anymore in real terms and that the potential dataloss due to non-journaling ext2 is more of a risk on a batter powered device.
 
Then I've read about TRIM but I'm not sure if it is on the version of ubuntu I'm using or if it only apples to certain ext versions?
 
Is using the 4GB SSD for a swap file a good idea?
 
Have I set this thing up correctly or is there a batter way? There's little or no data on it so reinstalling is fine.
 
Many thanks in advance.

---

### Post by dcstar on 2011-10-06
> **MobileTechie said:**
> I'm currently running Ubuntu 9.04 NBR on an Asus 901 with a 32GB Runcore SSD added to the existing 4GB PHISON SSD. The Asus has 2GB RAM.
 
I installed it using ext4 file system on the runcore SSD and using the 4GB SSD as the swap partition.
 
Since then I've been reading suggestions that one should not use ext4 on an SSD because the journaling will wear the SSD out too fast but then others say that doesn't apply anymore in real terms and that the potential dataloss due to non-journaling ext2 is more of a risk on a batter powered device.
 
Then I've read about TRIM but I'm not sure if it is on the version of ubuntu I'm using or if it only apples to certain ext versions?
 
Is using the 4GB SSD for a swap file a good idea?
 
Have I set this thing up correctly or is there a batter way? There's little or no data on it so reinstalling is fine.
 
Many thanks in advance.

9.04 is ancient and it's kernels will not support TRIM, only releases past 10.04 will.

---

