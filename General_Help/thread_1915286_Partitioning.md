---
title: "Partitioning"
date: 2012-01-25
forum: General Help
---

### Post by danielceleste on 2012-01-25
I was just wondering... how can i expand my main ubuntu partition?! i cannot do it through ubuntu, windows, or a disk mgmt bootable cd which has worked wonders in many other cases.

---

### Post by mörgæs on 2012-01-26
Hi, welcome to the fora.

Gparted is reporting something behind the red dot. What is that?

---

### Post by luckyEddy on 2012-01-26
You should check your indicated ntfs-partition from within windows, but it shouldn't break the resizing of the ubuntu-partition.

Did you try to resize the partition over the size of the extended partition? You should resize sda3 first and you should fill your drive with it. It doesn't make sense to keep empty space following to an extended partition.

Try to resize sda5 afterwards.

Best Regards

---

### Post by nipunshakya on 2012-01-26
I guess you wanted to use the unallocated space in your extended partition as swap-area...so its better you do that. Boot to liveCD, run gparted and make changes from there.
As far as the unallocated space of 34.70 gb, maybe u first need to handle your 3 gib area...and then goto windows' disk management utility(u don't need a bootable cd of it)....;right click my computer>manage> on the middle-left, select disk management and make a NTFS partition out of the big unallocated space.
I assume that since u don;t have a /home for your ubuntu, u are running out of space.... But if u create a NTFS out of that unallocated 34.70 gb, u can share that partition with windows and ubuntu as well.Goodluck

Regards,WinuxUser

---

