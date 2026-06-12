---
title: "No side by side part. option"
date: 2010-05-01
forum: General Help
---

### Post by Satchmo2 on 2010-05-01
So I'm trying to install the new ubuntu onto my friends hp mini 110, his hard drive is a 140 gig hdd with 100 gigs free, I've already defragmented(didn't help). In the install menu only two options appear, manually partition and use entire drive(erase xp). It thinks that the xp install is actually vista(for some reason). Gparted will not let me shrink the windows partition(only grow it). There is only one partition and a few megs unallocated.

---

### Post by WorMzy on 2010-05-01
I think you're best off booting into Windows, and using the [Windows disk manager]("http://support.microsoft.com/kb/309000#3") to resize the Windows partition, rather than trying to do it with GParted. Free up ~20GB, then install Ubuntu to most of the free space, and create a Swap partition (if necessary) in the rest.

---

