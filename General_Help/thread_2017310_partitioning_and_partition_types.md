---
title: "partitioning and partition types"
date: 2012-07-05
forum: General Help
---

### Post by disabled20191128 on 2012-07-05
Hi, I would like to dual boot my pc, i have 2x500Gb hdds one used for storing files and the other for Ubuntu.

That's how i am planning to partition the drives:

HDD 1 --> single partition called "storage" (500GB)
HDD 2 --> 1 windows partition (50GB), 1 ubuntu partition (447GB), 1 swap area (3GB).

I would like the storage drive to be visible only from ubuntu, and not from windows. So what filesystem type should i choose?ext4?

---

### Post by spikoley on 2012-07-05
EXT4 is your best bet.  You can still get around it in Windows, but I believe by default Windows will not be able to access it.

---

### Post by sudodus on 2012-07-05
> **Dennisgre said:**
> Hi, I would like to dual boot my pc, i have 2x500Gb hdds one used for storing files and the other for Ubuntu.

That's how i am planning to partition the drives:

HDD 1 --> single partition called "storage" (500GB)
HDD 2 --> 1 windows partition (50GB), 1 ubuntu partition (447GB), 1 swap area (3GB).

I would like the storage drive to be visible only from ubuntu, and not from windows. So what filesystem type should i choose?ext4?

1. If you are planning to use Windows for several years, I suggest that you use more than 50 GB, because it tends to increase due to update. I'd recommend 80 or 100 GB.

2. I'd suggest ext3 for the storage partition and ext4 for the root partition (/). You can also use ext4 for both of them. Both are well tested and none is visible from Windows unless you install special software for that purpose.

By the way, have you considered a separate /home partition?

---

### Post by disabled20191128 on 2012-07-05
No I haven't Should I?

---

### Post by sudodus on 2012-07-05
> **Dennisgre said:**
> No I haven't Should I?
Several people use it because it makes backup and upgrading to new versions simpler. I don't use it, I use a separate data partition similar to what you are planning to do. And I have symbolic links from my /home folder to that data partition.

But I just wanted you to know about it, and maybe search for some web pages describing it. For example, it is discussed in many threads here at the Ubuntu Forums. (Use **Search** -- Advance Search ...)

---

