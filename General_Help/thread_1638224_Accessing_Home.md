---
title: "Accessing Home"
date: 2010-12-05
forum: General Help
---

### Post by washable mist on 2010-12-05
i currently have both xubuntu 10.10 32-bit and windows 7 64-bit installed on my laptop which i use mostly for college work and basic programming (i'm still learning to program).

i have a 150gb partition with win7 installed, a 20gb partition with xubuntu installed and a 15gb partition with my linux home folder on, the rest of the space is unused because i thought i may need it for something else in the future.

the home folder partition is formatted to etc4, i now have a need to access this data from win7 for college work, i know that windows doesn't support mounting of etc file systems so i have hit a problem.

i thought about changing the type of partition from a ect4 to fat32 but will this delete my data?

or

are there any third party software packages for windows that will allow me to mount ect4?

---

### Post by SeijiSensei on 2010-12-05
> **washable mist said:**
> are there any third party software packages for windows that will allow me to mount ect4?

As I recall, the Windows driver for ext3 is pretty stable.  I'd try that.  FAT32 won't work because Linux expects /home to have a Unix file structure with permission bits, inodes, etc., that don't exist in Windows filesystems.

---

