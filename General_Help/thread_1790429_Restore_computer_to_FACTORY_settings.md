---
title: "Restore computer to FACTORY settings"
date: 2011-06-25
forum: General Help
---

### Post by Jishy on 2011-06-25
Well, my desktop's win7 installation stopped working over a year ago...so it just sat there gathering dust until the other night, when I was trying out ubuntu on it from a disk. 
So, well, the factory settings was vista, so i was wondering if there was something i could put into Terminal to restore it?
 
Thanks in advanced :)

---

### Post by Quackers on 2011-06-25
Welcome to UF :-)
Your computer may have a recovery partition which can be accessed by a pressing a certain key at boot time. You would need to look at the pc's documentation to find out which key or keys to press to access that. 
It is also possible that installing Ubuntu has over-written that partition.
Of course, if you made a set of recovery dvd's from your initial Windows installation, those can be run at any time to re-install.
Both of the above methods is likely to over-write your Ubuntu system.

---

### Post by Jishy on 2011-06-25
Nah, I didn't have any recovery DVD's. However, it seems there is at least 70gb of my HDD[it's 1tb, recognised as 930ish gb] So, could that be a recovery partition? 

If it helps, the make is a NEC Powermate V7330.

---

### Post by Quackers on 2011-06-25
I doubt it. That amount of lost space can disappear in formatting partitions.
If you can start gparted from a live session you may see if you have a recovery partition.
Have a look at your manual or do some googling for your machine and find out what key to press at boot time to access the hidden recovery partition.
It may be something like F10, F11 or ctrl+F11 or the del key. 
Then reboot and keep tapping that key and see what happens.

---

