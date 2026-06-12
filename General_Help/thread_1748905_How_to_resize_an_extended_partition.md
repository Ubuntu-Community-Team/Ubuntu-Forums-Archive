---
title: "How to resize an extended partition"
date: 2011-05-04
forum: General Help
---

### Post by ububeginner on 2011-05-04
Hi
I'm dual booting Win7 and Maverick and I'm running low on diskspace on my Ubuntu partition.
I booted into an Ubuntu 10.10 live CD and opened Gparted. After shrinking the storage partition I wanted to grow the extended ubuntu partition into the unallocated space to the left, but for some reason it won't let me do that.
Non of the partitions are mounted. 
please help me

---

### Post by ~Plue on 2011-05-04
You should first right click the swap partition > and click "swap off" //(the live CD would auto mount any existing swap partitions at boot)

---

### Post by ububeginner on 2011-05-04
Thanks, I knew it would be something obvious
Is there anything I should know about moving partitions, like Grub getting confused when the start of the ubuntu partition has moved to the left, or swap not being where it used to be

---

### Post by ~Plue on 2011-05-04
Afaik, grub would know where the boot files are as long as the device labels are left intact (resizing the the partitions wouldn't have any effect on them)

-good luck

---

### Post by wilee-nilee on 2011-05-04
> **ububeginner said:**
> Thanks, I knew it would be something obvious
Is there anything I should know about moving partitions, like Grub getting confused when the start of the ubuntu partition has moved to the left, or swap not being where it used to be

Generally you have to reload the mbr, I will presume grub2 here, so here is the link to load it from the live cd if needed.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

I'm not sure I would shrink that ntfs to be completely full, make sure that is a good idea.

---

### Post by dcstar on 2011-05-04
> **ububeginner said:**
> Thanks, I knew it would be something obvious
Is there anything I should know about moving partitions, like Grub getting confused when the start of the ubuntu partition has moved to the left, or swap not being where it used to be

Any change to the Swap partition will likely change its UUID and muck things up. Do a forum search for solutions to this.

---

### Post by satanselbow on 2011-05-04
Resizing the partition will not cause any problems as your entire ubuntu install in in one logical partition + swap ;)

Changing the order of the partitions would cause problems but apart from a long wait while your ubuntu partition (/sda6) shuffles to the left no harm will be done ;)

Just remomber that it will be a 3 stage operation

1) resize extended partition /sda3
2) move swap partition (sda5) to the left
3) move and resize /sda6 <--- may take a while to move 10G

good luck ;)

---

### Post by ububeginner on 2011-05-04
Ok
I resized the partitions, giving more space to the Ubuntu partition and booted just fine into both Win and Ubuntu.
However, after rebooting again, the PC just hung before ever reaching the Grub menu.

Anyway, I will mark this thread as solved as the partitions have been resized, although I have more serious problems now, but thats another thread.
[http://ubuntuforums.org/showthread.php?t=1749195](http://ubuntuforums.org/showthread.php?t=1749195) (just in case you're interested)

---

