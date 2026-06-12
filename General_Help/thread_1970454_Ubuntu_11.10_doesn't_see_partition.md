---
title: "Ubuntu 11.10 doesn't see partition"
date: 2012-05-01
forum: General Help
---

### Post by alenn on 2012-05-01
My partition suddenly dissapeared from Nautilus. Even GParted don't see it, in fact GParted is in mess. When I boot Windows, Windows can see all of mine NTFS partitions, but Ubuntu can't. And I repeat, everything was fine for many years using Ubuntu, but today suddenly my partition (I save documents on it) dissapeared. Can you help me

---

### Post by carranty on 2012-05-01
> **alenn said:**
> Even GParted don't see it, in fact GParted is in mess.[QUOTE]

Can you expand on this, what exactly is wrong with Gparted

[QUOTE=alenn;11894576]but today suddenly my partition (I save documents on it) dissapeared. Can you help me

Are you sure you can still see the partition from windows?  Have you tried booting into windows since the partition disappeared in Ubuntu to confirm all is still working (i.e. you can still open, edit and save files on the 'missing' partition)?

---

### Post by oldfred on 2012-05-01
Several years ago my entire sda drive disappeared in gparted. My XP still booted, but I ran chkdsk and then XP booted a tad faster and gparted would see it. 

I might try running chkdsk on all the NTFS partitions, c: d: etc to see if that makes any difference.

Ubuntu runs fsck every 40 or 60 reboots of the / partition. I do not think Windows schedules any chkdsks unless you have issues.

---

### Post by alenn on 2012-05-01
> **carranty said:**
> [QUOTE=alenn;11894576]Even GParted don't see it, in fact GParted is in mess.[QUOTE]

Can you expand on this, what exactly is wrong with Gparted



Are you sure you can still see the partition from windows?  Have you tried booting into windows since the partition disappeared in Ubuntu to confirm all is still working (i.e. you can still open, edit and save files on the 'missing' partition)?

yup, I'm sure. But I found a solution.

[http://askubuntu.com/questions/129153/ubuntu-11-10-dont-see-partition](http://askubuntu.com/questions/129153/ubuntu-11-10-dont-see-partition)

---

