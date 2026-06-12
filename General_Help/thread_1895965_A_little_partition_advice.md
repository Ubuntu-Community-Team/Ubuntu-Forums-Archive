---
title: "A little partition advice?"
date: 2011-12-15
forum: General Help
---

### Post by bradlees on 2011-12-15
.Greetings all,

I am learning my way through the pc and ubuntu world. I think I may have configured my partitions incorrectly when setting up the dual boot and installing ubuntu 11.10 on my pc. 

I dual boot between Win7 and oneric, what is the ideal/most effective or efficient number of partitions? There is also an hp recovery partition that was   on the pc and I read somewhere to keep this, which I did.

The partitions ubuntu is on sda5-8, ext 4, are split into 2 partitions and 2 swaps, limiting the hd space to the mounted portition, I'd like to use all the available space that is unmounted.

Any leads?

Cheers

---

### Post by corrytonapple on 2011-12-15
So you reserved space for a "Data Partition", correct?  Also, you do not need two swap partitions, so from an Ubuntu Live CD you can delete those.

---

### Post by zeroseven0183 on 2011-12-15
Hi! I too have Ubuntu and Windows sharing the same machine. The laptop has Windows pre-installed but I prefer using Linux as primary.

I have a 320 GB hard drive
 -- 200 GB of it is in NTFS
 -- 50 GB is Windows
 -- 23 GB is Ubuntu
 -- 12 GB is Lubuntu
 -- 4 GB is swap

then the other partition is for the HP recovery which I am thinking to remove in the near future.

The reason for this setting is so that whichever OS I boot into, I can access the files. I usually run virtual machines for testing and their files are in the larger partition.

You actually don't need two swap partition if you're thinking of dual booting Linuxes. One is enough.

---

