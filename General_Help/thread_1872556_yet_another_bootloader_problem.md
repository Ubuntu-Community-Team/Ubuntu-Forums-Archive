---
title: "yet another bootloader problem"
date: 2011-10-30
forum: General Help
---

### Post by poudigne on 2011-10-30
Here's my problem... i was on opensuse Gnome (last version) and since i didn't liked it I decided to switch back to ubuntu 11.10 and since then my Hard drive has no more bootloader

 I Experienced similar problem when installing ubuntu 11.10 over 11.04, and then installing kubuntu 11.10 over ubuntu 11.10. But i solved iby repairing grub with the disk repair tool, and doing some grub command to reconfigure it... both time it worked.

But now it just throw me another error > Error no activated partition after 3 hours of research and trying i"m finaly posting... Yeah i usually never post since i always figure out the problem by myself but im exausted,

Looking for the error on google links me to a lot of opensuse reference (it make sense!!) but most tutorial tells to reinstall opensuse or use opensuse live cd to  restore grub and link opensuse and blablabla opensuse blablabla opensuse again blablabla... welll... i dont want opensuse anymore i want ubuntu !! Lol

so if anyone want to help i will be happy, thnak you very much


sudo fdisk -lu gives 
> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa0d596e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    35653631    17825792   27  Hidden NTFS WinRE
/dev/sda2        35653632    35858431      102400    7  HPFS/NTFS/exFAT
/dev/sda3        35858432  1548928744   756535156+   7  HPFS/NTFS/exFAT
/dev/sda4      1548929022  1953523711   202297345    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1548929024  1951571967   201321472   83  Linux
/dev/sda6      1951574016  1953523711      974848   82  Linux swap / Solaris

Disk /dev/sdb: 3185 MB, 3185573888 bytes
98 heads, 62 sectors/track, 1024 cylinders, total 6221824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c65ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     6221823     3110881    c  W95 FAT32 (LBA)


---

### Post by WasMeHere on 2011-10-30
Hello poudigne,

It will be easier to help if you give some more details about your system(s). I understand that you have Kubuntu 11.10. What is on your computer now? Single or multiple boot? Valuable data files or only a fresh system? ... Please explain and also post the output of the following command
```
sudo fdisk -lu
```

Have fun finding out about *ubuntu :-)
Olle

---

### Post by poudigne on 2011-10-30
And  what I currently have on my hard drive, is my recovery partition, windows 7, and ubuntu 11.10, the only valuable data files I have is my recovery partition wich makes my computer still on warranty,

---

### Post by WasMeHere on 2011-10-30
Will the following link give you some new ideas?

[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files_[/COLOR]]("https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files")

---

### Post by poudigne on 2011-10-31
This tutorial was exactly the thing I did to restore my grub the first time (it took 3hours et make it work)

Why... this... page don't comes up in first place when looking for "grub" and "error" on google !!!

With those 2 commands line, took 3 min to repair my grub and boot on my linux !! :)

A BIG FAT EPIC thank to you Olle Wiklund :KS:KS

---

### Post by WasMeHere on 2011-10-31
You are welcome, I am happy that I could help you.

Please mark the thread SOLVED

Have fun
Olle

---

