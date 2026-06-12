---
title: "Dual Boot Help"
date: 2009-07-29
forum: General Help
---

### Post by Grannun on 2009-07-29
I used to be dual booting vista and 9.04, but I finally said hell with Vista and got rid of that partition.  Problem is, in order to do so I had to move the swap and extend the ext3 partition and now even though there is 2gb of swap space, ubuntu doesn't realise it!  How do I fix that?

Second, grub loads the boot menu every time I boot up even though it doesn't have to.  How do I change that since there is only one OS now?

Thanks,

Ubuntu noob

---

### Post by cybrsaylr on 2009-07-29
Because 9.04 installs so fast, I'd simply save what you want, then do a fresh reinstall.

---

### Post by hamstersquasher on 2009-07-29
Swap answer - make sure that your swap partition is listed in /etc/fstab.  Alternatively, you can just use swap *files* instead of swap *partitions*.  

Grub answer - you can modify the /boot/grub/menu.lst file so that the 'timeout' line has a 0 at the end of it instead of a 10 (for ten seconds) or whatever.

---

