---
title: "Unusable and undeletable partitions"
date: 2012-05-12
forum: General Help
---

### Post by tejaskale on 2012-05-12
About 3 weeks ago, I installed Ubuntu 12.04 Beta 2 in my Dell Inspiron N4010 laptop. But for reason unknown to me, it kept on rebooting. Hence I reverted back to 11.10 and decided to wait for the stable release of 12.04. Once the stable release came out, I installed it on my machine. Now, due to some naivety on my part during the installations and removals, two read-only partitions of size 476MB and 3.01GB were created by taking space from the root partition (Screenshot attached - Look at '/dev/sda6' and '/dev/sda8'). I ignored it initially but now I can't since the 'Low Disk Space' pop-up comes up quite regularly. 

I tried deleting the partitions using GParted but got the error message that I need to unmount all partitions with numbers smaller than these two partitions. Doing so would mean unmounting the root partition which is not possible. 

Can anyone suggest a way for me to merge these two unnecessary partitions with my root? Or do I need to reinstall the Ubuntu system all over again?


Thanks for your help.

[[IMG]http://thumbnails62.imagebam.com/18980/7c83a3189790234.jpg[/IMG]]("http://www.imagebam.com/image/7c83a3189790234") 

[IMG]http://www.imagebam.com/image/7c83a3189790234[/IMG]

---

### Post by wilee-nilee on 2012-05-12
Use a live ubuntu cd, and you only need one swap. Any partition can be resized, and you can remove the swaps and make another when you're done adjusting. When you boot the cd make sure all partitions are not mounted.

---

