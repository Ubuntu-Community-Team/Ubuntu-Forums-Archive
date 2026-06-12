---
title: "moving a partition"
date: 2011-05-11
forum: General Help
---

### Post by enimeizoo on 2011-05-11
Hello,
I want to move my / partition to the end of my drive (sda). To do this with gparted, I have to unmount it, but I'm not comfortable with the idea of unmounting root partition... Should I do it from a live cd? More important : is the operation safe?

---

### Post by Praveen30 on 2011-05-11
> **enimeizoo said:**
> Hello,
I want to move my / partition to the end of my drive (sda). To do this with gparted, I have to unmount it, but I'm not comfortable with the idea of unmounting root partition... Should I do it from a live cd? More important : is the operation safe?

every operation is safe, if you do it correctly..
[https://help.ubuntu.com/community/HowtoPartition/MovingPartition](https://help.ubuntu.com/community/HowtoPartition/MovingPartition)

---

### Post by Quackers on 2011-05-11
It is not really a recommended modification, but I've done it before. With earlier versions of Ubuntu it would cause problems with grub. However the later versions use the UUID of the partition rather than its designation (like sda5 for instance) so it's much less problematic.
You definitely need to do it from the live desktop, not your normal desktop. You may alse need to turn swap off (right-click swap partition and choose "swapoff".
Depending on its size the operation could take up to 2 hours.

---

### Post by srs5694 on 2011-05-11
> **Praveen30 said:**
> every operation is safe, if you do it correctly..

I must disagree with this statement -- strongly! Safety is relative, and 100% safety is impossible to achieve. Even if you make multiple backups, store some of them offsite, and take every other conceivable precaution, it's possible that some series of disasters will wipe out all your data. You can improve safety up to some value -- 90%, 99%, 99.9%, or whatever, but never to 100%.

Moving data around on a hard disk is inherently risky. Power failures, bugs, existing but undetected data corruption, and other problems can cause data loss. Backups can help you recover from such problems, but that just adds to the hassle factor. You have to ask yourself if it's really worth the hassle. To answer that question, of course, you must also know why it is you want to do whatever it is you're trying to do. For instance, are you hoping to improve performance? Do you want to clear up room for another OS installation? Do you want to make your partition layout more tidy? You haven't said, and you haven't told us anything about the current layout (a screen shot of GParted or the output os "sudo fdisk -lu" would help a lot), so we can't make any judgments.

That said, I'm generally reluctant to move partitions around without very compelling reasons to do so. As a general rule, such operations take longer than you're likely to gain in improved performance, especially when you consider the risk of lost time should the operation fail. Other reasons might or might not be compelling.

Concerning unmounting root (/): It's impossible while the system is running. Go ahead and try; you'll just get an error message. To unmount root, you must reboot with another system (such as an Ubuntu installation disc in "live CD" mode), in which case what's normally root (/) becomes just another partition that you can mount or unmount at will.

---

### Post by enimeizoo on 2011-05-11
Well, it's done, without a problem it seems. I needed to do it because I managed to reach the maximum amount of partitions on the first drive, having 300GB unallocated. That was not a problem until now, since I want room to try new OSes out. 
Just to know, providing my home folder is on a separate partition, what do I keep/loose if I loose the root partition?
Thanks anyways.

---

### Post by Quackers on 2011-05-11
You lose the "system" minus your home files and config files. ie all the system files, grub files etc etc.
Glad things worked out ok :-)

---

