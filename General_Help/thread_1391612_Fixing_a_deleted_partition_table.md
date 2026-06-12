---
title: "Fixing a deleted partition table"
date: 2010-01-27
forum: General Help
---

### Post by McVonstein on 2010-01-27
Hello!  A few minutes ago, I erased my partition table.  Can anyone recommend a good method of reconstructing it?  And if this is impossible, can anyone recommend a good method of data recovery?  
I had an ntfs partition with windows 7 and a larger ext3 partition that ran Debian.

Thankyou for the help!

Jon.

EDIT

I'm running Test-disk on the SystemRescueCD at the moment (cross your fingers).  Suggestions would still be appreciated!

---

### Post by efflandt on 2010-01-27
It is always a good idea to run **sudo fdisk -l** (small L as in list) and save or print that somewhere safe before tampering with partitions, because then you can use fdisk to recreate them "exactly" as they were, and data will still be there if not formatted or overwritten.

I had a problem long ago where 64-bit WinXP Pro beta changed my partition table from 240 heads to 255 heads and different cylinders, such that 64-bit WinXP could not even boot itself, much less XP Home.  And I had told it to use an existing partition, so it should not have even tampered with partitions.  I had originally used fdisk to create partitions for 64-bit XP and Linux after shrinking XP Home with ntfsresize from a Linux rescue CD, but unfortunately did not record fdisk settings.  So I had to do some trial and error from memory (in my head) with expert fdisk settings before I got everything to boot properly (no data loss).

Then when I started to install SuSE (8.2?) at the time I recognized from numbers it posted that it was about to do the same thing 64-bit Win had done, so I used its advanced mode to tell it not to touch the partition table, but just use what I had already set up.

I hear TestDisk often mentioned.  Good luck.

---

