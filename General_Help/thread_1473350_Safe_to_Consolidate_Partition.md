---
title: "Safe to Consolidate Partition?"
date: 2010-05-05
forum: General Help
---

### Post by Martin Mendoza on 2010-05-05
:KS Hello,

I almost lost all my data using a partition tool (can't remember) part of a System Rescue CD I downloaded off the internet.

I was just wondering, why can't I consolidate my partitions by deleting all the others and extending the size of my main partition (/ext2), is it because it's mounted?

If so, I was considering using the UNR LiveCD and extending my main partition there to fill up my whole HD space. Will this work?

Thanks a lot ya'll...

---

### Post by gzarkadas on 2010-05-05
As a general advice, _always make backups_ of your data _before performing partition operations_; many things can go wrong.

Assuming you did that step, then yes you can use the Live-CD to boot the computer and then type in a terminal:
```
sudo gparted
``` to open gparted.

Inside gparted: 
1. select your hard disk device
2. unmount any partitions that appear mounted
3. proceed to the desired partition operations

gparted can move partitions around without losing the data on them. But if you want to _consolidate partitions, all data on them will be lost_. So make sure you have backups before proceeding.

---

### Post by Martin Mendoza on 2010-05-05
> **gzarkadas said:**
> As a general advice, _always make backups_ of your data _before performing partition operations_; many things can go wrong.

Assuming you did that step, then yes you can use the Live-CD to boot the computer and then type in a terminal:
```
sudo gparted
``` to open gparted.

Inside gparted: 
1. select your hard disk device
2. unmount any partitions that appear mounted
3. proceed to the desired partition operations

gparted can move partitions around without losing the data on them. But if you want to _consolidate partitions, all data on them will be lost_. So make sure you have backups before proceeding.

Is it possible to consolidate by deleting [FONT="Courier New"]/ext3[/FONT] and [FONT="Courier New"]/ext4[/FONT] then resizing [FONT="Courier New"]/ext2[/FONT] and not lose data on [FONT="Courier New"]/ext2[/font] ?

---

### Post by warfacegod on 2010-05-05
> Is it possible to consolidate by deleting /ext3  and /ext4 then resizing /ext2 and not lose data on /ext2 ?

Yes (make a backup!). Gparted can do this. You'll have to do this with a LiveCD or USB. Simply unmount and delete the partitions you don't want and then right click the remaining partition and select Resize/Move. You can drag the arrows on the left or right of the partition "picture" or you can enter numbers into the text areas.

---

### Post by john newbuntu on 2010-05-05
Just to add, the resizing operations could potentially be time consuming depending on the data.  Do not cancel or power-off during this, which is why it is important to backup data just in case.

---

### Post by Martin Mendoza on 2010-05-05
Awesome! Thanks a lot... was a little bit apprehensive of doing that. :guitar:

---

### Post by warfacegod on 2010-05-05
As long as you make a backup (you can never say that enough times), pay attention to what you are doing and follow the instructions in this thread, you should be fine.

---

### Post by Martin Mendoza on 2010-05-06
Done. Now I have just one partition for all.

Thanks again.

---

