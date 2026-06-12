---
title: "HELP PLZ! Format new external 2TB HDD - use with ps3, ubuntu desktop and windows xp/7"
date: 2011-03-30
forum: General Help
---

### Post by kaisar89 on 2011-03-30
Hi, I just bought a Seagate Expansion 2TB HDD which i hooked up to my **[COLOR=Red]ps3[/COLOR]** and was not  recognised. I googled the problem and found out i need to format the HDD to fat32. **[COLOR=Red]How do format the HDD in Linux Ubuntu?[/COLOR]**

I also want to use the HDD on windows XP/7 and Ubuntu. [COLOR=Red][B]What format does the HDD need to be to work with all 3 operating systems?
[/B][COLOR=Black]
i will use the HDD mainly for HD movies so the files more than likely will be above 4gb.[/COLOR] [B]how can i play these files? can i connect the the HDD to tv via usb port? (LG 50PK350)

[/B][COLOR=Black]any help would be much appreciated, i will await a response before formatting / partitioning the drive.

Thank you in advance.
[/COLOR][/COLOR]

---

### Post by kaisar89 on 2011-03-30
bump. please help

---

### Post by Krytarik on 2011-03-30
If at any possible you should format the disk to NTFS instead of FAT32, because
- the max. file size of FAT32 is 4 GB
- the usual max. partition/volume size of FAT32 is 32 GB
- FAT32 is much more susceptible to disk errors than NTFS
- FAT32 wastes a lot of space when storing many small files at big partitions, although that seems to be the case in your application

[http://en.wikipedia.org/wiki/Fat32](http://en.wikipedia.org/wiki/Fat32)
[http://www.theeldergeek.com/ntfs_or_fat32_file_system.htm](http://www.theeldergeek.com/ntfs_or_fat32_file_system.htm)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

You can use GParted, or even "System -> Administration -> Disk Utility" to format the disk.

All of those 3 OS can handle both FAT32 and NTFS.

> **kaisar89 said:**
> [COLOR=Red] **how can i play these files? can i connect the the HDD to tv via usb port? (LG 50PK350)**[COLOR=Black]
[/COLOR][/COLOR]What exactly do you mean by that?

---

