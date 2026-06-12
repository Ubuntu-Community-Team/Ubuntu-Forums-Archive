---
title: "Excessive HDD use jbd2 journaling"
date: 2012-05-23
forum: General Help
---

### Post by dejang on 2012-05-23
I am having problems on Ubuntu 12.04 x64 "fresh" instaled on ext4 partition on primary HDD. When not in use every 5 to 10 seconds HDD is active for about 10 seconds an writing no mater what aplication is turned on or running. I used iotop and found that jbd2 is constantly writting to HDD. The noise of HDD is driving me crazy, at this rate disk will not last long. On the same HDD I have Win 7 (dual boot Grub2) and everything works OK, disk is turned off when not in use, computer is silent. Everything else is working fine in 12.04 (just litle problems with skype and webcam, but that is torelable), but fear from loosing disk and noise is untorelable since I have computer turned on for 10 hours a day...
I tried manualy to lower the frequency of journaling, but no solution found on web helped me so far, disk is grinding at same rate.
Any solution of this problem? If not I think I will be forced to stop using Ubuntu, no HDD will last long at rate of use and the noise from HDD is not tolerable...

---

### Post by zero2xiii on 2012-05-23
Hay,

A quick google gave these possible solutions:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607560](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607560)

[https://bbs.archlinux.org/viewtopic.php?id=113516](https://bbs.archlinux.org/viewtopic.php?id=113516)


Note the comment in the launchpad page:
> After much investigation, i discovered that the output of "hdparm -B /dev/sda" happen to be my only laptop hard drisk, gives me a value of 128, which permits the HD from spinning down. This is what is prevents the hard driver from spinning down and not the jbd2 activity. BTW, I did a complete fresh install.

from hdparm man page (notice the bit about 128 being in the range that prevents spinning down):

   -B Query/set Advanced Power Management feature, if the drive sup&#8208;
               ports it. A low value means aggressive power management and a
               high value means better performance. Possible settings range
               from values 1 through 127 (which permit spin-down), and values
               128 through 254 (which do not permit spin-down). The highest
               degree of power management is attained with a setting of 1, and
               the highest I/O performance with a setting of 254. A value of
               255 tells hdparm to disable Advanced Power Management altogether
               on the drive (not all drives support disabling it, but most do).

This seems be a general issue and fix from most of the forums I read through. But it seems to be a kernel 2.6 bug, should have been fixed by the 3.2 kernel. Strange.

Cherz

---

### Post by dejang on 2012-05-24
Tryed to edit fstab and commit=600, no change. I am using 3.2 kernel, so this bug is not solved as for me. Reinstaling doesnt help either. I hate it, but for now I am setting grub to win7 default system and hoping that some future update will solve this problem

---

### Post by zero2xiii on 2012-05-25
> **dejang said:**
> Tryed to edit fstab and commit=600, no change. I am using 3.2 kernel, so this bug is not solved as for me. Reinstaling doesnt help either. I hate it, but for now I am setting grub to win7 default system and hoping that some future update will solve this problem

Hay,

Did you try the post I qouted? If you read through the two links you would have seen that the "commit=60" helped very few people, and it was not the only possible solution.

Hope an update does get released.

Cherz

---

### Post by pbrane on 2012-05-25
Are you sure it's a journal write? If you have hddtemp installed it looks like a hard drive access each time it samples the hdd temperature.

---

### Post by dejang on 2012-05-30
> **zero2xiii said:**
> Hay,

A quick google gave these possible solutions:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607560](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607560)

[https://bbs.archlinux.org/viewtopic.php?id=113516](https://bbs.archlinux.org/viewtopic.php?id=113516)


Note the comment in the launchpad page:


This seems be a general issue and fix from most of the forums I read through. But it seems to be a kernel 2.6 bug, should have been fixed by the 3.2 kernel. Strange.

Cherz

dejan@dejan:~$ sudo hdparm -B /dev/sda6
[sudo] password for dejan: 

/dev/sda6:
 APM_level    = not supported
dejan@dejan:~$ 

I also checked the hddtemp and it is not instaled on my system.

No idea what to do:confused:

---

### Post by ziggo0 on 2012-06-28
I'm having this same problem...only solution I've read is to disable journaling at the disk of dataloss and that isn't even an option. I built a 12tb NAS with 8x2tb hdds, mdadm raid6 and freshly formatted with mkfs.ext -m 0 -- it sits there all day and night grinding away...currently on Ubuntu Server 12.04 - completely updated. Mount options are noatime & barrier=0...I've tried removing them both but it didn't help. Server was priory on ubuntu 10.04 without this issue...updated for the upgrade in software but now I'm entirely regretting it.

---

### Post by supremebot on 2012-12-03
I have same prblem with 4 x 2 tb disks in software raid5 its pretty noisy with wd's black edition. 
I also tryed the commit=60 and commit=600 but still grinding on every sec. 

tic tic tic tic every sec, it look like the commit=60 works because when i look in iotop jdb2 is not called as frequently but its still noise and im sure its also power comsuming.

i hope some one finds a solution soon.:confused:

---

### Post by supremebot on 2012-12-03
I found the solution in another forum the, solution be is to be patient.:P

"To update this - it's finally stopped. After much research I finally came across a tid bit of information stating that when you format an ext4 partition it's basically a 'quick' format...and over time it slowly 'formats' the rest of the drive. For large volumes like mine (12TB) it can take an extensive amount of time. It finally seems to be done and things are back to normal"

i think it can take days... depending on the size of the raid ofcause, its funny i cant see what is going on in iotop.

I hope it helps u all.:)

---

### Post by Apelord on 2013-05-21
Hi, 
I appreciate this thread is quite old, but has there been any resolution or conclusion to this issue? I have the same problem.. I am running Ubuntu 13.04, kernel: Linux 3.8.5-030805-generic (x86_64). Some posts suggest this is not a bug but just a feature caused by some process using jbd2, others that it is a result of quick formatting and the jbd2 activity is simply continuing the formatting job (and will presumably stop or become less frequent).

---

