---
title: "Reinstalling GRUB2 after Win7"
date: 2009-12-25
forum: General Help
---

### Post by The_Shady_1 on 2009-12-25
I just finished installing Win7 and I'm trying to get GRUB back.How can I get GRUB back and playing nicely with Win 7? Tried GRUB 2 Basics without any luck.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32f932f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60802   488282112    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79907b78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       42804   343823098+   7  HPFS/NTFS
/dev/sdb2           42805       60801   144560902+   5  Extended
/dev/sdb5           42805       60065   138648951   83  Linux
/dev/sdb6           60066       60801     5911888+  82  Linux swap / Solar

Win7 + Karamic

---

### Post by HappyFeet on 2009-12-25
[Reinstalling Grub2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by Leppie on 2009-12-25
boot from a livecd, then run these commands:
```
$sudo mount /dev/sdb5 /mnt
$sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by The_Shady_1 on 2009-12-25
I got GRUB back now (Thanks Leppie). My GRUB menu shows XP in the list when I dont have XP installed anymore. How do I get it to show Win 7 instead of XP?

---

### Post by drs305 on 2009-12-25
> **The_Shady_1 said:**
> I got GRUB back now (Thanks Leppie). My GRUB menu shows XP in the list when I dont have XP installed anymore. How do I get it to show Win 7 instead of XP?

Is it a title error or something more serious? When selected, does it boot to Win 7? Have you tried running "sudo update-grub" to see if it picks up the correct title?

If it's just the title that is wrong, here are some things you can do:
1. Leave it like it is.
2. Copy the entry to a custom file (/etc/grub.d/40_custom) and manually change the title. You can make the file 06_custom to have the menuentry appear at the top of the screen.
3. Change part of the 30_os-prober file in the same directory. You can take a look at the "G2 Tweaks" link in my signature line for ways to change the titles of various entries. (Only for those who don't mind getting into the details of the G2 scripts)

Added: The user in a PM indicated that the title was correctly displayed after running "sudo update-grub".

---

