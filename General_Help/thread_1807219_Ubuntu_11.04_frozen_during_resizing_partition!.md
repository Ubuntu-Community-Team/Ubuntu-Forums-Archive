---
title: "Ubuntu 11.04 frozen during resizing partition!"
date: 2011-07-18
forum: General Help
---

### Post by PloXyZeRO on 2011-07-18
Hi. I'm having a problem. This is my first time using Ubuntu, so I don't really know much about it. I tried installing it from a DVD earlier, but it wouldn't work. Then I tried on my flash drive, still didn't work. I realized that the downloaded iso  (Ubuntu 11.04 64 bit) was only 411 MB instead of 698 MB. I then tried to download it again, and it was the correct size. 

I booted it off my flash drive, and tried to install. It asked how much of the HDD space I wanted to reserve for Ubuntu, I think. I can't quite remember, but I dragged it over to 30 GB. Now I realize that I don't actually need that much, oh well. I got an error, can't quite remember what it said, but then the same window came up again asking to resize the partition. There was only about 20 GB availiable this time (instead of the 320 before), I reserved 6 GB, and clicked continue. I checked back after like 3 hours and the window is white and frozen. 

Is there any way I can restart my laptop and correct the issue without messing anything up? I'm not really sure what I did wrong.

If it matters, I'm installing it on an Alienware M11x laptop.
I'm not quite sure, but I think the specs are
Nvidia GeForce 335M
320 GB HDD
i5 U520M processor @ 1.07 GHz (ranked over 3.0 GHz)
Windows 7 64-bit

If there's any other information you need, just ask and I'll try to tell you. PLEASE help! Thank you in advance :D

---

### Post by PloXyZeRO on 2011-07-18
Sorry, I hate to bump, but I'm getting a little bit worried. I have to do some work for my robotics team, and all of the files are there. I'm afraid to turn off my laptop though since it was resizing the partition at the time it froze. I still can move the mouse around and stuff and change my system settings and everything, but the window that had the resizing partion options is just completely white and I get a loading mouse icon when I put my mouse over it.

Can someone please tell me if it's safe to reboot my laptop?

---

### Post by Mark Phelps on 2011-07-19
So, you had important work to do, and you STILL messed with your PC??  And, you didn't back up your "robotics team" files, first?

When you used GParted to shrink the Win7 OS partition, you most likely corrupted it ... so now, it's likely to NOT boot anymore.  

In your hurry to install Ubuntu, you DID ensure that you first went into Win7 and used the Backup feature to create and burn a Win7 Repair CD, right?

About all you can do now is borrow a Win7 DVD from someone who has Win7, boot from that, and attempt to run Startup Repair.  You may have to run it three times.

If you're lucky, that will repair the filesystem and you'll be back working again.

Otherwise, you would need to boot from an Ubuntu LiveCD, connect an external drive to your PC, and attempt to copy the files you need from your Win7 OS partition to the external drive. That's likely NOT to work, though, because if the filesystem is corrupted, Ubuntu is likely to refuse to mount the partition.

---

