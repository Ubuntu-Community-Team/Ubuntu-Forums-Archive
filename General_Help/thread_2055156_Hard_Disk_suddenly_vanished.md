---
title: "Hard Disk suddenly vanished"
date: 2012-09-08
forum: General Help
---

### Post by satish_j on 2012-09-08
I know this may not sound to be Ubuntu-related but i need urgent help with my system.
I have 2 HDD on my system out of which one is for data storage,consists of 3 Partitions(all NTfS formatted)The other HD
stores Lucid,Precise & XP.
Today,when i booted into Lucid,i found that the 2nd HD(data HD)is not getting detected in Nautilus.I rebooted the system
and checked in Bios and both the HDs are showing up  in Bios.
Booted into XP and there also,the data HD was missing.
I remember the last operation i did on that HD was a simple data copy operation into it.
What could have caused my HD to suddenly become invisible from both OS.
Appreciate quick reply/help on this..

---

### Post by oldfred on 2012-09-08
I would try chkdsk from Windows first.

Change c: to whatever drive it is, if three partitions you have to run at least 3 times, and rerun if any errors until no error as it does not fix everything on one pass:

chkdsk C: /r

---

### Post by satish_j on 2012-09-09
I got my issue resolved after a lot of googling.
TestDisk Utility came to my rescue and helped me recover the lost disk drives back.
Thanks agian..

---

