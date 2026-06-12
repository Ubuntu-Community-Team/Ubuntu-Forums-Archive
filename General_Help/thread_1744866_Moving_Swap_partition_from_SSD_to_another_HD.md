---
title: "Moving Swap partition from SSD to another HD"
date: 2011-04-30
forum: General Help
---

### Post by nrabett on 2011-04-30
The title pretty much sums it up. I need to move the Swap partition because my PC refuses to hibernate when this partition is smaller than my RAM. 

Currently, the Swap partition is on the same SSD as the Ubuntu /.

I do not want to waste 8GB of my SSD for this purpose, and if I am not mistaken, I can simply create a new Swap partition on my storage HD with Gparted, delete the current Swap partition and restart the PC. Can someone confirm this before I potentially start messing up my system?

I have also read about Swap files (instead of partitions). Currently, I have a 200 GB ext4 partition on the storage HD - could I enable hibernation by simply creating a "swap file"?

---

### Post by lithopsian on 2011-04-30
Surprised nobody answered this since it is very easy.

Yes, you can hibernate to a swap file.  It is easy to create one or more swap files and easy to change them later.  You must use a special command to create the file to make sure it is suitable to be used as swap:
```
dd if=/dev/zero of=/swap bs=1024k count=4096
```The count parameter is in kB, so make it the size you need.  You can add it to your fstab or you can mount it manually.  You will need to use mkswp and swapon.  To use the swap file for hibernation you will need a package called uswsusp.

When you are happy with your new swap file(s), or new swap partitions if you want to do that, then you can just delete the one on the SSD from your fstab.  Then you can merge that partition into your /root, or use it for something else.

I doubt that you need 8GB of swap.  The "twice main memory" rule of thumb is 10 years out of date.  You need swap equal to your main memory for hbernating, and you might need another gig or so for paging.  Once you are using a gig of swap then you will desperately want to shutdown some stuff.  If you have hundreds of gig spare then you can have more swap just as a safety net.  I would suggest perhaps creating a swap partition to use for hibernation and then a swap file for general swap.  You can set the priority so that the swap file is used first and the partition will only be used to hibernate or in a desperate emergency.  Then you can easily change the amount of paging space later by adding more swap files or by replacing the one you have.

---

