---
title: "partion hard drive."
date: 2010-07-03
forum: General Help
---

### Post by kduffy101 on 2010-07-03
sorry if this has already been asked....
im new to ubuntu,i came from vista+wiped hard drive on install of ubuntu,
ive got 114gb free on hd,iwant to partion 50gb so i can install xp on it.
how do i do it without wiping ubuntu?
any help would be great.thanks

---

### Post by artemyv on 2010-07-03
> **kduffy101 said:**
> sorry if this has already been asked....
im new to ubuntu,i came from vista+wiped hard drive on install of ubuntu,
ive got 114gb free on hd,iwant to partion 50gb so i can install xp on it.
how do i do it without wiping ubuntu?
any help would be great.thanks

1. To free space for XP you can do the following:
- boot from live cd
- start the gparted (System -> Administration -> GParted)
- resize your partition freeing nessacary space

It would be good to bacckup your data before messing up with the disk in case of problems

2. You can format the free space in Gparted using ntfs and than install xp on that partition

or

you can install XP on the free space

3. Probably - XP will clean up your grub (boot manager) - so you'll be unable directly boot to Ubuntu. You should read the thread about restoring grub after installing windows and do required preparations beforehand.

---

### Post by oldfred on 2010-07-03
Link to how to reinstall:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Just be sure to make the NTFS partition a primary (sda1-sda4) or windows will not see the partition to install.

---

