---
title: "8GB partitions for Ubuntu"
date: 2011-10-07
forum: General Help
---

### Post by Jimfox on 2011-10-07
I was going to install a Ubuntu on an 8GB flash drive I have, The swap partition should be twice the since as the ram, I have 6 gigs of ram and I can't put 12GB of swap space on the flash drive, So for ubuntu what should my partitions be like if the root is 4.4 minimum?

---

### Post by haqking on 2011-10-07
> **Jimfox said:**
> I was going to install a Ubuntu on an 8GB flash drive I have, The swap partition should be twice the since as the ram, I have 6 gigs of ram and I can't put 12GB of swap space on the flash drive, So for ubuntu what should my partitions be like if the root is 4.4 minimum?

today it is debatable as to whether you need swap at all on a normal system.

either way you dont need to setup swap on a flash drive.

i have a 2gb with 11.04 on which runs just fine

---

### Post by oldfred on 2011-10-07
On my 16GB flash I used 8GB for / and left the other 8GB for data. I have 4GB of RAM and it runs without swap. Of course it is not my main install and I will not run any of the heavy duty appications or lots of applications at once that might require swap.

While not an SSD as it is much slower you still want to do similar settings.

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

