---
title: "cloning root drive from large to small partition"
date: 2010-11-12
forum: General Help
---

### Post by ugruntu on 2010-11-12
i am running ubuntu 10.10 and windows7 on a asus eee 1015. currently i have two partitions: 80GB for windows (NTFS) and 160Gb for Ubuntu (ext4).

I want to: 
- shrink the windows partition (easy, no worries);
- Shrink the ubuntu partition 
- join the space thus created in a third partition that i can use for storage, media etc accessible by both windows and ubuntu

The problem:
- i could not manage to get gparted live to run off USB stick (i get the unable to find medium.... error)
- even if i would get gparted to work and i succeed in shrinking the ubuntu partition as well, the two spaces reclaimed will be divided by the ubuntu partition, which means they cannot be joined in a third partition.

so here is what i want to do:
- shrink windows and create a new partition;
- format this new partition as ext4;
- somehow "clone" the data on my current ubuntu root into the new partition;
- format the current root as NTFS and use it as the storage partition

i am aware this may mean i would have to re-set grub etc (which i worry about but should be doable with help from this forum), but would the cloning of the partition be possible? please note that i would need to clone data from a 160G partition into a 40G partition.

any advice?

BY THE WAY - forgot to mention that i have tried to load clonezilla off an USB drive and i get the same error: "unable to find medium..."

---

### Post by ugruntu on 2010-11-13
someone? anyone?

---

### Post by ugruntu on 2010-11-13
nevermind - sorted. was embarrassingly easy: a matter of booting in ubuntu live with the start disk, running gparted. sorted.

---

### Post by C.S.Cameron on 2010-11-13
Yes booting the Live CD or Live USB is the way to go.

---

