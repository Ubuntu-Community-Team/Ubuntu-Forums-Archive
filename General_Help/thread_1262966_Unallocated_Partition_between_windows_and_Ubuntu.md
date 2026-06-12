---
title: "Unallocated Partition between windows and Ubuntu"
date: 2009-09-10
forum: General Help
---

### Post by kseunder84 on 2009-09-10
Is there any way I can extend my Ubuntu partition into the unallocated? The screenshot shows what I have now, it's taken in Ubuntu, I know I have to unmount, which I did before on Ubuntu Live CD. I had Windows taking up the space, so I moved windows down to 25 GB and I wanted to use all the rest of my hard drive for Ubuntu. Anyone know how I can do this?

---

### Post by CatKiller on 2009-09-10
It's not unallocated, it's a partition of unknown type. Whatever you did before didn't work.

If you're confident that you don't want whatever's on that partition you can delete it. Then the space will be unallocated and you can expand your Extended partition and then the partitions inside it into that unallocated space.

---

### Post by kseunder84 on 2009-09-10
I've tried that already, I don't know if I'm doing something wrong or not. I deleted the partition and it changes to unallocated. Then when I click on my Ubuntu partition, the sda5 ext3, it lets me click on move/resize but only thing I can do is make it smaller, not larger.

---

### Post by drs305 on 2009-09-10
> **kseunder84 said:**
> I've tried that already, I don't know if I'm doing something wrong or not. I deleted the partition and it changes to unallocated. Then when I click on my Ubuntu partition, the sda5 ext3, it lets me click on move/resize but only thing I can do is make it smaller, not larger.

As catkiller stated, you must first expand the extended partition (sda2) Select it by clicking on it in the bottom pane. Once you have done that, you should be able to expand your Ubuntu partition (sda5). 

Of course, this must be done while the Ubuntu partition is unmounted, so use the LiveCD or SystemRescueCD, Gparted CD, etc. In your screenshot, the partitions are all still mounted, as indicated by the "keys" icon next to the partition in the lower pane.

---

### Post by kseunder84 on 2009-09-10
I did what catkiller said, deleted the partition but it still will not let me extend my Ubuntu (sda5). When I click on the unallocated it gives me the option of new, nothing else. When I click on my Ubuntu partition, I click move/resize, but it won't let me resie it at all, it's at 56 GB and won't go any higher, only lower. I can extend my windows partition, sda1, but I don't want to extend that any further.

---

### Post by drs305 on 2009-09-10
> **kseunder84 said:**
> I did what catkiller said, deleted the partition but it still will not let me extend my Ubuntu (sda5). When I click on the unallocated it gives me the option of new, nothing else. When I click on my Ubuntu partition, I click move/resize, but it won't let me resie it at all, it's at 56 GB and won't go any higher, only lower.

You must expand the extended partition first! This is sda2 and has a light blue border. Before you do anything with the unallocated space or with sda5, **you have to select sda2** on the lower panel and then drag the light blue border to the left to get the unallocated space *inside* the light blue box.

---

### Post by kseunder84 on 2009-09-10
alright thank you sorry about that. I've got it now. Thank you everyone!

---

