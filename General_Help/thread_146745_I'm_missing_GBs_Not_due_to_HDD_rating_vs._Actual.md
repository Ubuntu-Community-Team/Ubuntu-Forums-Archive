---
title: "I'm missing GBs: Not due to HDD rating vs. Actual"
date: 2006-03-18
forum: General Help
---

### Post by anths on 2006-03-18
I have 2 250GB hard drives. When formatted in windows using Fat32 they were 233GB - now that I have moved on to Linux and have them formatted to ext3, they display as ~218GB. What is the deal with this? I didn't change anything on the hardware, just a software change so why would I lose 15 GB per drive and can I get them back? I have reformatted each drive atleast twice and always end up with the same result.

- Anthony

---

### Post by NeghVar on 2006-03-18
Is there any limit as to how much Ubuntu/ext3 will recognise on each drive?

If so, have you tried cutting them in half to see if they total closer to 250?

---

### Post by hw-tph on 2006-03-19
By default Linux will reserve 5% of ext2/ext3 partitions for the root user. You can change this using tune2fs, and also look into the sparse_super option and see if that's something you want to use.


Håkan

---

### Post by anths on 2006-03-19
Ok I will look in tune2fs. Before I do I was poking around and found out a few things when I looked at the partitions using GparteD. The actual partition itself does show 239,XXX MB but it shows the 20GB missing as in use. When I mount the drive and view the capacity of space used in the folders it adds up to 190GB while it shows 210GB used in GparteD. I reformatted one of the drives again just to make sure and right from the start it says that the 20GB are in use regardless of what I do.

5% of this space would be roughly 12GB, not the 20GB that is "in use" but I am going to look into tune2fs and this spare_super option now.

---

