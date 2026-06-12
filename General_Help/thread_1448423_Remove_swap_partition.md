---
title: "Remove swap partition"
date: 2010-04-06
forum: General Help
---

### Post by a mad pigeon on 2010-04-06
I have a bit of a problem here with the swap partition. I want to free up a partition so I can install another OS later on, as I'm using up all four partitions (2 Windows, 1 Ubuntu, 1 extended swap). Any idea how I can disable and unmount the current swap and make a swap file instead? Thanks.

Currently swap isn't being used, I have 3GB of memory. Do I even need a swap file?

---

### Post by karmic-koala on 2010-04-06
> **a mad pigeon said:**
> 
Currently swap isn't being used, I have 3GB of memory. Do I even need a swap file?

Normally you do won't need swap, I have 1.3gig and my system's never used more than .6gig. But should a rogue process temporarily need more memory you want to have a contingency plan in form of swap. Usually 1gig of swap would do so you can use the other 2 to store files, etc.

If you do not have swap at all, processes, if they need it, will be denied memory, which can at least in theory crash your computer.

---

### Post by a mad pigeon on 2010-04-06
I can understand that and why even though none of my swap space has been used in the last 5 months. But how can I unmount my swap partition, create a swap file and mount it? I think I know how to unmount it.

---

### Post by oldfred on 2010-04-06
You can keep the swap as it is in extended. You have to expand the extended anyway unless you are going to use space from somewhere else. Then you could delete swap and remove it from fstab and recreate in the new extended partition and add it back to fstab with the new UUID.

---

### Post by a mad pigeon on 2010-04-06
How do I expand the extended partition? I have 50GB of space that's not partitioned, but I need to free up a primary partition for another OS to use.

---

### Post by karmic-koala on 2010-04-06
You'll have to create a LIVE CD off something like partition magic or gparted, reboot and then work from there.

---

### Post by a mad pigeon on 2010-04-06
Ah, I tinkered with Gparted and somehow I was just able to delete the partition with no errors, thought it would return an error for 'in use' or something like that. I hope there's no errors when I reboot... Thanks for helping guys.

---

### Post by oldfred on 2010-04-06
Unless you deleted the fstab entry for swap it will give an error and may not let you  boot. If you have problems use the liveCD to edit /etc/fstab.

---

