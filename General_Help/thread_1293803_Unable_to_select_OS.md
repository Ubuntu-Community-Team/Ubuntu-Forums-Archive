---
title: "Unable to select OS"
date: 2009-10-17
forum: General Help
---

### Post by somersjr on 2009-10-17
Hi. I just installed Ubuntu 9.04, dual boot Vista 64. While installing, I had a keyboard and mouse. Now, the keyboard and mouse don't work so I can select the operating system. 
 
I change the default to Vista 64 for now. The keyboard and mouse are Microsoft Wireless Laser Keyboard 7000 (combo). I also tried attaching a USB keyboard, which did not work.
 
The keyboard and mouse worked in Ubuntu once it was loaded and work in Vista 64.
 
Any suggestions? I sure would like to play with Ubuntu and possibly move to it exclusive once I get it fully up and running.
 
Thanks
 
S.

---

### Post by oldfred on 2009-10-17
I had this problem when I updated my system and it was BIOS settings. In my case I was able to plug in the mouse & keyboard to the ports and it worked. By changing a setting in BIOS (I forget which but something about USB mouse & keyboard) both grub & Ubuntu worked without any problems since.

---

### Post by somersjr on 2009-10-17
> **oldfred said:**
> I had this problem when I updated my system and it was BIOS settings. In my case I was able to plug in the mouse & keyboard to the ports and it worked. By changing a setting in BIOS (I forget which but something about USB mouse & keyboard) both grub & Ubuntu worked without any problems since.
 
Thanks for the reply.  Unfortunately, no keyboard I have tried works, so can't access the bios.
 
I can't even try to update Ubuntu.  During install, I told it to use 50% of my drive for a partition (250 gig) and it created a much smaller partition instead, so when I tried to update, I got a message that there is no disk space.  
 
Now that I've changed the default to Vista 64, I can't go back to Ubuntu because I have no keyboard...lol
 
Looks like I'll have to toast Ubuntu and try to go back to Vista 64.  It's a shame.  I would have liked to work with it.
 
S.

---

### Post by oldfred on 2009-10-17
Did you by any chance switch mouse & keyboard. I have done that many times, the new color code connections only help some. USB has solve my problem. Nothing in Ubuntu should modify mouse or keyboard settings in Windows. You would literally have to mount the windows partition and delete stuff.

The default install uses only 2.5GB. You are supposed to move a slider to give it the amount of space you actually want.

HOWTO: 2.5 GB System Partition - What Went Wrong? 
[http://ubuntuforums.org/showthread.php?p=7658271](http://ubuntuforums.org/showthread.php?p=7658271)

---

### Post by somersjr on 2009-10-17
> **oldfred said:**
> Did you by any chance switch mouse & keyboard. I have done that many times, the new color code connections only help some. USB has solve my problem. Nothing in Ubuntu should modify mouse or keyboard settings in Windows. You would literally have to mount the windows partition and delete stuff.
 
The default install uses only 2.5GB. You are supposed to move a slider to give it the amount of space you actually want.
 
HOWTO: 2.5 GB System Partition - What Went Wrong? 
[http://ubuntuforums.org/showthread.php?p=7658271](http://ubuntuforums.org/showthread.php?p=7658271)
 
I fixed the keyboard and mouse problem.  Just did a hard reset on the motherboard and its working now and I can access both operating systems... woo hoo!
 
How do I increase the size of the partition?  Does Ubuntu have a utility?

---

### Post by oldfred on 2009-10-17
You cannot increase the size of a partition you are using, so the standard install does not include gparted. If you have additional drives unmounted you can download gparted from synaptic.

You can use the  live CD or download a gparted liveCD for editing partitions. Resizing can take time,  if it is a new install it may be quicker just to delete the 2.5GB partition, make a new larger partition and use manual install to tell it to use the larger partition already created. You could just delete and reinstall but adjust the slider to give you more space.

---

