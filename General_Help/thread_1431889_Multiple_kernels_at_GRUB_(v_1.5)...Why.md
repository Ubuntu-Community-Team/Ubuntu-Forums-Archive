---
title: "Multiple kernels at GRUB (v 1.5)...Why?"
date: 2010-03-17
forum: General Help
---

### Post by siemprepeligroso on 2010-03-17
Dear Friends,
After I messed up badly with my netbook I have to reinstalll the OS, it is a government property netbook that came up with Edubuntu 7.04 insalled on it. I shouldn't mess with the filesystem but I did and now I have to install Edubuntu from the beginning, but I must be sure that everything will just like I have done no change, so I am afraid that I can make some mistakes at this point
The first thing that I want to know is: Why there are multiple kernels listed at the 
GRUB (v 1.5)...this is the full list:

[FONT=Fixedsys][SIZE=1]Ubuntu, kernel 2.6.28.9 Default
Ubuntu, kernel 2.6.28.9 Default (recovery mode)
Ubuntu, kernel 2.6.28.9 
Ubuntu, kernel 2.6.28.9 (recovery mode)
Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)
Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)
Ubuntu, memtest86+[/SIZE][/FONT]

[FONT=Verdana]Now I wonder how can I get this also after I reinstall the OS, plus this time I will try to make dual boot with xp installed first[/FONT].

Thanks in Advance :smile:

PS: Also when I access the HDD from livecd Ubuntu 9.10 the partitions listed are:

/dev/sda1 ext3 [File System] 146.19 GiB [size] 6.42 GiB [used] boot [Flags]
/dev/sda2 extended 2.86 Gib ---- -----

(under /dev/sda2  afer expanding appears: )
 /dev/sda2 linux swap 2.86 Gib ---- -----


waht about this LINUX SWAP

---

### Post by bobcollard on 2010-03-17
First it is common for there to be more than one kernel showing in Grub.  It is a good idea to leave at least one earlier kernel that works in case there is an upgrade that causes problems so you can fall back on it at startup.  It is difficult and dangerous to modify grub unless you know what you are doing.  There are all kinds of todos in Google for it, make sure you add the version of grub to your searches.  A swap file is like additional RAM that the System can fall back on if you are overloaded.  Although they are seldom used if you have 4GB or more of RAM, many Linux users have older systems and need this extra memory.  Hope this steers you in the right direction.

---

### Post by siemprepeligroso on 2010-03-19
I formatted my PC and installed WinXP first, and on the partiotion manager I left a space of 3GiB free space for Linux SWAP, now I will install Edubuntu 9.10, how do I define this space to the Ubuntu OS as SWAP, or I have just wasted 3 Gib of my HDD

---

### Post by bobcollard on 2010-03-19
> **siemprepeligroso said:**
> I formatted my PC and installed WinXP first, and on the partiotion manager I left a space of 3GiB free space for Linux SWAP, now I will install Edubuntu 9.10, how do I define this space to the Ubuntu OS as SWAP, or I have just wasted 3 Gib of my HDD
The installer will take part of the "Empty Space" and make it's own swap file  Unless you specify all of your partitions. It has to be done at installation.

---

### Post by xifer on 2010-03-19
once you have linux installed you can use the partition manager to pick up that space for your swap file.  But you probably don't need 3 Gig for it so you may be able to extend your main linux filesystem to take some of this space and use 1 or 2 GB for swap.  Or you may get option to partion during the install - I don't recall right now.  Worst case boot from a live CD and format the disk as required then install Edubuntu.

---

