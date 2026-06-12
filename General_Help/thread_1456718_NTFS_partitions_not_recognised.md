---
title: "NTFS partitions not recognised"
date: 2010-04-17
forum: General Help
---

### Post by Levo on 2010-04-17
Hi there,

On my system I have two internal SATA Disk drives, the first one is 120GB and the second one 360GB.

120GB Disk:
1st partition: NTFS (22GB), Windows XP is installed, for playing my games.
2nd partition: NTFS (62GB), The "GAMES" partition, where all the games are installed
3rd partition: EXT4 (25GB), Ubuntu Karmic
4th partition: SWAP space

The 320GB disk is a single NTFS partition, where all my data/files are stored.

Here's my problem: A couple of days ago I used GPARTED to shrink the 320GB partition and create a new 2GB FAT32 one at the end of it. (Never had any problem before using GPARTED for any filesystem). I put in there some old dos games and rebooted to windows. Then I formatted a diskette as MS-DOS startup disk. I rebooted the computer again and and booted from the FreeDOS LiveCD. After playing for a while I tried the MS-DOS disk, to see if it performed better. Now Windows XP does not recognise the DATA and GAMES partitions, buts recogninses the fat32 one. In ubuntu they work, but when I try to fix them, it says "run chkdsk". Windows does not recognise them so I cannot do this. Any suggestions?

P.S.: I tried to restore Windows XP from a Norton Ghost Backup image file, but its LiveCD does not recognise these partitions either (norton ghost 12 uses vista to boot the live cd).

---

### Post by Levo on 2010-04-18
Bump

---

