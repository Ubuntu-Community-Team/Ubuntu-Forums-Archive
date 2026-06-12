---
title: "Partition problems"
date: 2009-07-24
forum: General Help
---

### Post by The Toxic Mite on 2009-07-24
Many hellos to you all.
 
I want my Ubuntu-powered desktop to dual boot with FreeDOS, but I have a little problem;
 
I am trying to create a new partition on GParted. But when I click "Create partition table" on the Device drop-down menu, a warning pops up saying that EVERYTHING will be deleted.
 
I know it can be a little off-putting, but I really want to create a new partition so that I could put FreeDOS on it.
 
-TTM-

---

### Post by plucky on 2009-07-24
> I am trying to create a new partition on GParted. But when I click "Create partition table" on the Device drop-down menu, a warning pops up saying that EVERYTHING will be deleted.

Post a screenshot of your gparted window so that we can see how your disk partitions are setup.

If it is just one partition with Ubuntu on it,then all you have to do is **resize** the partition,not create a new partition table.You will probably need to use the Ubuntu Live CD if it is your / system partition as the partition has to be un-mounted before you can resize it.

Good Luck

---

### Post by Psycho.mario on 2009-07-24
You need to click 'Resize & Move' (I think that is what is says) on your current partition, make it smaller, and create a new partition in the new 'unallocated space'.

---

### Post by The Toxic Mite on 2009-07-24
> **plucky said:**
> Post a screenshot of your gparted window so that we can see how your disk partitions are setup.
 
If it is just one partition with Ubuntu on it,then all you have to do is **resize** the partition,not create a new partition table.You will probably need to use the Ubuntu Live CD if it is your / system partition as the partition has to be un-mounted before you can resize it.
 
Good Luck
 
It was just the one with Ubuntu on it, so I resized it and made a new partition. It now has FreeDOS on it!
 
Thanks!

---

