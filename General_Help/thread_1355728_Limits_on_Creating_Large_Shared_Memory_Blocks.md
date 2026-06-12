---
title: "Limits on Creating Large Shared Memory Blocks?"
date: 2009-12-15
forum: General Help
---

### Post by jbmck on 2009-12-15
I am trying to create a large block of shared memory using shm_open and mmap. I'd like to make the block of memory quite large, much more than 50% of the installed RAM. But while shm_open, ftruncate, and mmap all return successfully, I get a segmentation fault if I try to access the block of shared memory beyond a certain point. Clearly the memory is not really all allocated even though mmap returns successfully. Since I am running in a virtual machine, I can easily vary the amount of memory that is available, and I find that the maximum amount of shared memory that is really there is 0.5 * RAM - 1900 (in units of pages.) What sets this maximum and how can I make it larger? A straight-forward malloc works fine.

I've tried altering the usual suspects, shmmax and shmmni to no avail. I've tried changing the overcommit ratio to no avail. What controls the limits on the size of a shared memory block???

---

### Post by dang_boy on 2011-12-28
updated

---

### Post by Bobhuber on 2011-12-28
> **dang_boy said:**
> updated
shm   /run/shm      tmpfs     nodev,nosuid,noatime,mode=1777,size=6G        0      0

---

### Post by Iowan on 2011-12-28
From Code of Conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

