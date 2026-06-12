---
title: "Wubi install problem"
date: 2011-02-15
forum: General Help
---

### Post by SinSkinner on 2011-02-15
Hi everyone,   I installed Ubuntu 10.10 using XP and Wubi.  I have 350 GB hard disk, C partition for XP, and D partition for mp3, movies, pics  etc.  And Ubuntu is installed on D disk (30 GB space is separated for Ubuntu).
Now,  in Ubuntu, I can't see D disk, only part of D disk that is separated for Ubuntu files.  I can see C disk with XP instalation, but no D, where is my music, movies etc.
Any help is welcomed :)

---

### Post by Rubi1200 on 2011-02-15
Hi and welcome to the forums :-)

> The Windows partition where you installed Wubi is available as /host  within Ubuntu (Places > Computer > File System > Host) All the other partitions will be available under Places > Removable Media 
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?)

Can you see them now?

What file-system do you have on D; NTFS?

---

### Post by SinSkinner on 2011-02-16
I somehow missed that part in wubiguide :)
txn a lot, I see it now.
D: partition is in NTFS

---

### Post by Rubi1200 on 2011-02-16
> **SinSkinner said:**
> I somehow missed that part in wubiguide :)
txn a lot, I see it now.
D: partition is in NTFS
Excellent! Glad things are sorted out :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

One more thing:

make sure you lock the grub packages to avoid issues with Wubi breaking as a result of GRUB updates:
[https://wiki.ubuntu.com/WubiGuide#Warning](https://wiki.ubuntu.com/WubiGuide#Warning)

---

### Post by SinSkinner on 2011-02-16
Done and done  :)

---

