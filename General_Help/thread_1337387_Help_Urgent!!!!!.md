---
title: "Help Urgent!!!!!"
date: 2009-11-25
forum: General Help
---

### Post by BAMF1501 on 2009-11-25
OK so i got windows 7 installed o my 1 tb HDD And wanted to try ubuntu out so put it on my 80 gb hdd but now i can only boot into my 80 gig not my 1tb with windows 7 what do i do ??

---

### Post by doas777 on 2009-11-25
ok, does the bootloader give you an option for windows boot? Grub doesn't replace ntldr, but it does replace the mbr, so to boot into windows, you have to select it from grub.

if that is not the issue, please open a terminal, and paste in:
```
sudo fdisk -l
```
so we can see your partitions.

---

### Post by BAMF1501 on 2009-11-25
it does not giv eme an option to boot into windows cause i have windows on a seperate HDD The 1 tb and ubuntu on a 80 gb hdd

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x841f841f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74927128+  83  Linux
/dev/sda2            9329        9730     3229065    5  Extended
/dev/sda5            9329        9730     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6668e566

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7feae7d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    b  W95 FAT32

---

### Post by doas777 on 2009-11-25
well, it will give you the option even if it is on another disk, as long as everything is working correctly. I have several systems running in the fashion. 
it looks like your tb drive is fine, so hopefully it is just a matter of reconfiguring grub to know that it is there.
[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html)
[http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html](http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html)

just remember, Karmic uses grub2, so some instructions regarding file locations and whatnot may need interpretation.

---

### Post by mr clark25 on 2009-11-25
if you unhook the 80GB hdd, will it boot to windows? you might try that and jusy use that for now...

---

### Post by BAMF1501 on 2009-11-25
i tried that ^^ no worky

---

