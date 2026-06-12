---
title: "Deleted the 2 non NTFS partitions and now i cant boot"
date: 2011-01-16
forum: General Help
---

### Post by razercultmember on 2011-01-16
the error at boot up is

grub no rescue (something something something)

i went into partiton manager in windows 7 and deleted the ubuntu partitions, the swap and the main, thinking it would delete ubuntu :\

i really need to keep all my data on the windows 7 partition

help? ](*,)

---

### Post by b0b138 on 2011-01-16
Grub reads files on the partition you deleted to boot. You need to restore the windows mbr


[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by wilee-nilee on 2011-01-17
If you need a W7 recovery disc here is a link. Run the startup repair 3 times, or use the command line to run.
```
bootrec.exe /fixmbr
```

Same as the above posts link to MS.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

There is also a bootloader named lilo that can be loaded from a live Ubuntu cd with these two commands.

Restore basic windows boot loader - universe enabled
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

