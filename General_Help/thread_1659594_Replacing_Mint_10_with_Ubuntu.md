---
title: "Replacing Mint 10 with Ubuntu"
date: 2011-01-04
forum: General Help
---

### Post by Mercenary(FH) on 2011-01-04
So I have Windows 7 and Mint 10 installed on my Desktop, im installing Ubuntu 10.10 on my laptop, and I typically like to keep the Distros the same.

Is there any SAFE way of removing Mint and installing ubuntu? obviously it's using GRUB (i forget which version) without having to reinstall my Windows 7

---

### Post by mastablasta on 2011-01-04
backup data
boot live CD and gparted
delete mint partition
install ubuntu there
update grub

---

### Post by Mercenary(FH) on 2011-01-04
Oh Ok so i'd Use the Ubuntu live CD and delete mint from The Ubuntu Live CD.

THEN just replace the partition in gparted?

how do u update GRUB?

---

### Post by Bucky Ball on 2011-01-04
No need to replace the partition in Gparted. You can do all this as part of the Ubuntu install when you get to that bit. You will be able to wipe Mint and install Ubuntu in the free space (or over it). Use EXT4 for the partition's file format. ;)

---

### Post by Dans564 on 2011-01-04
yea, as bucky ball said this can all be done from within the ubuntu installer.  No need to boot the complete live environment.

---

### Post by lindsay7 on 2011-01-04
post the results of sudo fdisk -l  that is the lower case letter L,

If you have a separte root or / partition and a/home partition already set up, then all that you would need to do is install ubuntu to the root or / partition and you would leave the other partitions alone.  This would keep your data and most setting.

---

### Post by cascade9 on 2011-01-04
Mint 10 is based on 10.10, and uses the ubuntu repos so apart from some interface changes and a few tweaks done by the mint devs, its pretty much the same. Is it really worth reinstalling?

---

### Post by Mercenary(FH) on 2011-01-04
Actually it's mint 9, lemme go do the fdisk and post it here

edit: fdisk results
Device Boot    start    end     blocks      id       system
/dev/sda1 *      1        13      102400     7        HPFS/NTFS
Parition 1 does not end cylinder boundary.(wtf does this mean)
/dev/sda2        13        32711   262644353+   7     HPFS/NTFS
/dev/sda3        32711     38914    498k        5     Extended
/dev/sda5        32711     38654     477k       83    Linux             
/dev/sda6        38654     38914      2082816   82    Linx swap/ something


had to do this in recovery mode....my normal linux wasn't booting lol

---

### Post by Mercenary(FH) on 2011-01-04
bump with new fdisk info. is this still possible?

---

### Post by lindsay7 on 2011-01-05
You do not have a separate home partition. So you will have to do a new install for Mint.

---

### Post by TBABill on 2011-01-05
All you should need to do is install Ubuntu 10.10 to sda5, format it (mark for formatting using the installer on the LiveCD), mark it to be root "/" and then install. If you do want /home on a separate partition then you will have to resize, but that can be done via the installer as well. As long as you target the same partition (sda5) with the new OS, formatting and setting as root and installing will clear out the old OS on that partition.

---

