---
title: "Remove Grub"
date: 2010-08-27
forum: General Help
---

### Post by 572094 on 2010-08-27
I've had ubuntu installed on my system but removed it. If I try to start my computer (which should have Windows 7 on it) it gets "grub rescue>", due to that the only OS I have available is ubuntu from a CD (without actually installing) seeing as it won't load Windows. How can I remove grub? I searched on google but nothing I found works.

I suppose it's not just removing file system/boot/grub, I'm afraid doing that might screw my computer up even further.

---

### Post by wojox on 2010-08-27
You need to repair the Mbr. Without a Windows CD/DVD your gonna need [Ultimate Boot CD]("http://www.ultimatebootcd.com/")

You could try this as well [Download Windows 7 System Recovery Discs]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by 572094 on 2010-08-27
I have the Windows 7 recovery disks but I haven't been able to do anything other than installing (which doesn't seem to overwrite Grub).

I'll try the Ultimate boot CD if I can figure out how that works.

---

### Post by deserthowler on 2010-08-27
> **572094 said:**
> I've had ubuntu installed on my system but removed it. If I try to start my computer (which should have Windows 7 on it) it gets "grub rescue>", due to that the only OS I have available is ubuntu from a CD (without actually installing) seeing as it won't load Windows. How can I remove grub? I searched on google but nothing I found works.

I suppose it's not just removing file system/boot/grub, I'm afraid doing that might screw my computer up even further.

Have you tried fdisk /mbr command from windows to remove grub?

Earl

---

### Post by oldfred on 2010-08-28
From a windows repair screen and then the command line:

BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub

Or from Ubuntu you can install a generic boot loader that will boot windows.

Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by 572094 on 2010-08-28
The Windows 7 system recovery disks worked, I had to use a command thing and type: "**Bootrec.exe /FixMbr**".

Thanks for the help.

---

