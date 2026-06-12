---
title: "regular problem, permanent fix?"
date: 2011-01-04
forum: General Help
---

### Post by Muskiet on 2011-01-04
I regularly run into the problem that some of my programs won't start and I found out many months ago that running "rm /var/cache/apt/*.bin" solves this problem.
Lately I've had to do this more frequently and I was wondering if somebody could please explain to me why it happens and if there is a permanent fix?

My Ubuntu version is 10.04

---

### Post by Brandon Williams on 2011-01-05
That sounds to me like either your root partition or your /var partition (if they are different) may be full. When you're having the kind of trouble that has been driving you to delete those files, use the command df to check how much free space you have. Are any of the partitions at or near 100% in use? Deleting those files would clear such a condition temporarily, but a better solution would be to figure out what is really using up your disk space, since those files are somewhat big, but not so big that they would be the real source of the problem. If you discover that one of your partitions is close to full, use the utility du to attempt to figure out where all the partition's space has gone.

---

