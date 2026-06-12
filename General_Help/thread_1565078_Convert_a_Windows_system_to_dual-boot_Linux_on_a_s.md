---
title: "Convert a Windows system to dual-boot Linux on a second drive"
date: 2010-08-31
forum: General Help
---

### Post by Nikolai D. on 2010-08-31
Hi guys, need your help please :)

I'm trying to get a dual boot system. And my situation is exactly as the situation described is this article:

[http://www.linux.com/archive/feature/113945](http://www.linux.com/archive/feature/113945)

So i'm just following it. But but when i try to load Linux from the NTLDR i just get this error:

BootPart 2.60 Bootsector (c) 1993-2005 Gilles Vollant [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
Loading new partition

Bootsector from C.H. Hochst„tter

Cannot load from harddisk.

Insert Systemdisk and press any key.


Any suggestions?
Would be very appreciated. :)

Thank u,
Nikolai

---

### Post by inso_741 on 2010-08-31
you are trying to make the NT loader boot ubuntu instead of using grub....which BTW works flawless with both the OS and you can get better support for it from the forum...as for the above method try asking in windows forums

---

### Post by jmore9 on 2010-08-31
On my dual boots i put linux on the second, slave drive and windows on the primary, first drive.  I install grub to the mbr of the first drive.

If i want to get rid of linux i format the second drive and do the following from command line :

fix mbr
then 

fix boot

I think thats the order i do them.  I only run Ubuntu by it self now.

---

