---
title: "Ubuntu hangs and capslock+scrollLock blinking"
date: 2010-07-26
forum: General Help
---

### Post by satish_j on 2010-07-26
After installing XP and Ubuntu(Hardy heron)on a new HD,i have been facing several issues with the system.
On logging to Ubuntu,it runs for some 5-10 minutes and then freezes completely.SrollLock and capsLock keys on keyboard keep on blinking..Googled and came to know that this can be kernel related issue..
Worst part is:after facing this,when i try to login to XP,it runs without the accelerated video drivers(which were previously installed)..I install the drivers again and reboot--->XP now runs in proper display mode-->login to Ubuntu,it gain freezes and on restarting again,XP runs without acc. vid drivers.
I guess this is related to Motherboard drivers..After installing XP,i install the m/b drivers from the CD i got with it.But,how to install the drivers for Ubuntu???
Any help seriously appreciated??/

---

### Post by sikander3786 on 2010-07-26
Hi.

I think this is some hardware issue. I had Windows Server installed on a system whose Graphics Chip was going bad (but I didn't know it), the system used to run well for about 5-7 hours before hanging. When it was restarted, the Video Drivers were gone. I thought of putting Ubuntu on to it and Ubuntu could never boot into GUI. Only thing I could get was a console. (Mean Ubuntu is good at understanding problematic hardware than Windows)

So, please check for some unusual heat on any of the chips on your motherboard. (The reason behind XP forgetting the drivers could be same to mine).

HTH.

---

### Post by satish_j on 2010-07-26
But,it was working fine on old HD..If the problem is of over-heating,then XP must also freeze after some time..
Only thing i have changed on my system is the HardDisk.And i cannot accept the problem with a new HD..
BTW,can anyone tell me how to check the kernel logs after system is booted??
I want to post the same here so that anyone can help me find the problem causing factor..

---

### Post by sikander3786 on 2010-07-26
Follow the link.

[http://ubuntuforums.org/showthread.php?t=10508](http://ubuntuforums.org/showthread.php?t=10508)

---

### Post by satish_j on 2010-07-26
OK,iam shifting the topic to a new direction which i think may be the cause of the prob..
i need now some help for instaling HardyHeron with XP..i remember last day when i installed it,i selected the 'manual' option from hard disk partitioning and created a partition of unused disk space and formatted it using ext3 FS.
Also,initially,i selected 'use largest continuous free space' option,but i got some error related to partition table/size not defined.
very first option is 'use entire disk',which i assume will erase XP if selected..
Any ideas??

---

### Post by sikander3786 on 2010-07-26
Ok.

The best option is of course the manual partitioning option. You need to create the following partitions.

1. 512MB, ext3, Mount Point /boot
2. XXXGB, ext3/ext4, Mount Point /
3. RAM X 2 (or whatever space you dedicate as SWAP), Mount Point SWAP

Remember this is the basic configuration. You can always have separate partitions for /home /var etc. but that is something advanced.

I think you will be ok with this.

HTH.

EDIT: Use entire disk will of course remove all data.

---

### Post by satish_j on 2010-08-03
Thanks sikander,your first guess was right..
It was faulty RAM that was the problem.One of the RAM sticks(out of 2)got damaged.System is running fine with a single RAM stick.
BTW,In last 1 month,i have faced many hardware issues with my system..may be it's time to go for a new one..

---

