---
title: "Incorrect/Extra Swap"
date: 2012-05-01
forum: General Help
---

### Post by sillypants on 2012-05-01
I used to have a 4GB swap partition.  I booted GParted, deleted it and merged with a consecutive partition to create a 6.3GB swap partition.  Then when I booted, I hadn't changed the UUID in fstab so it wasn't using the swap partition.  However, it was still reporting 4GB of swap.  Once I corrected my fstab, the swap size jumped to 4GB+6.3GB = 10.3GB.  Did Ubuntu make a swap file without me telling it to?  I searched the hard drive and didn't find anything.  How do I fix this?

I am running ubuntu 10.04 if that matters.  Thanks for any help!

-toan

---

