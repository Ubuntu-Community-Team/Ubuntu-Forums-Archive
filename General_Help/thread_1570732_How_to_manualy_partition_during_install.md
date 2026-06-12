---
title: "How to manualy partition during install"
date: 2010-09-08
forum: General Help
---

### Post by OpressedCalamity on 2010-09-08
Hello, I hear xfs is much faster then ext4, But whne I try to manualy partition I don't know what to set mount points to.. how many swap partitions to make, can someone give me step by step instructions? thanks.

---

### Post by bodhi.zazen on 2010-09-08
> **OpressedCalamity said:**
> Hello, I hear xfs is much faster then ext4, But whne I try to manualy partition I don't know what to set mount points to.. how many swap partitions to make, can someone give me step by step instructions? thanks.

You can use xfs , you need to set a mount point such as / for the root partition or /home if you want it as a home partition.

You only need one swap partition.

Be warned :

1. Most people will not see much, if any, performance boost between various file systems.

2. Read any online stats with a grain of salt. How many times do you create then delete 10,000 1 Kb files ?

3. I advise you choose a file system based on features, not performance stats.

4. Be warned, IMO XFS is more vulnerable to data loss with power failures then other file systems.

---

### Post by OpressedCalamity on 2010-09-08
Thanks

---

### Post by OpressedCalamity on 2010-09-08
> **bodhi.zazen said:**
> You can use xfs , you need to set a mount point such as / for the root partition or /home if you want it as a home partition.

You only need one swap partition.

Be warned :

1. Most people will not see much, if any, performance boost between various file systems.

2. Read any online stats with a grain of salt. How many times do you create then delete 10,000 1 Kb files ?

3. I advise you choose a file system based on features, not performance stats.

4. Be warned, IMO XFS is more vulnerable to data loss with power failures then other file systems.
what should the mount point of swap be?

---

### Post by Rubi1200 on 2010-09-08
Lot to go through here, but I agree with bodhi that > features, not performanceis probably more important:
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by OpressedCalamity on 2010-09-08
So, guessing the experts opinion is better then mine, i'll stick with ext4, thanks.

---

