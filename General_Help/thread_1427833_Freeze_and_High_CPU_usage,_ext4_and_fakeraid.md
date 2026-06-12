---
title: "Freeze and High CPU usage, ext4 and fakeraid"
date: 2010-03-12
forum: General Help
---

### Post by mononom on 2010-03-12
Hello.

I'm using Karmic koala 9.10 64bit.
Have three HDD, WD Raptor 36GB X 2 and Seagate 160GB.
2 WD Raptors are striped (RAID 0), and all hdds are formatted by ext4.
(Intel ICH9R raid)

Problem is that, when reading/writing hdd heavily, system freezes a moment or very very slow down. When I used a windows XP, there's no problem. 
Moreover, one other machine, Karmic Koala 9.10 64bit and ext3, no raid, works very fine.

My system consists of,

Intel C2Q Q6600
2GB DDR2 6400 (1GB X 2)
Gigabyte P35-DS3R
Geforce 8500GT 256MB
WD Raptor 36GB X 2 (Intel RAID-0)
Seagate 160GB
24" and 20" Dual monitor (Twinview, 1920x1200 and 1600x1200).

And, i'm using compiz, also.

If I format my hdd and re-install ubuntu, does it become better?
or, if I use software raid provided by linux kernel, or if i don't use a raid?


Sorry for poor english.

---

### Post by otnateos on 2010-04-10
hi there, did you end up figuring what was the problem with the slow down? i am considering to have similar setup like yours ext4 + RAID0 and investigating any issues that may come up with that setup.

---

### Post by mononom on 2010-04-10
> **otnateos said:**
> hi there, did you end up figuring what was the problem with the slow down? i am considering to have similar setup like yours ext4 + RAID0 and investigating any issues that may come up with that setup.
I changed the system configuration, instead of using intel Raid0, I'm currently using just a LVM partition of 2 raptors. that makes the situation better and the system freezes fewer times than previous, but, freezing still occurs.

---

