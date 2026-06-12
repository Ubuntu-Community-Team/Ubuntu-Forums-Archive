---
title: "can't boot to XP -- GRUB problem"
date: 2009-09-21
forum: General Help
---

### Post by rygar on 2009-09-21
Hi, I'm having a problem booting to XP.

Previously, I had XP and Vista installed.  One of the options in GRUB was to start Vista bootloader, which let me choose between XP and Vista.

I have since uninstalled Vista and formatted that partition.  However, the Vista bootloader remained.  So, I attempted to get rid of it (using VistaBootPRO) by deleting the vista bootloader and installing the xp bootloader.

Now, GRUB still starts when I boot my computer, but the option for Windows XP gives me a blank screen.  After about 15 seconds, my computer reboots.

I wanted to try "fixboot" from the XP cd, but the XP cd gives me a blue screen.  For the record, I can access my XP drive fine from Ubuntu.

How can I fix it so that GRUB loads to XP?  How can I fix the XP boot sector from Ubuntu?

Thanks!!
Jeff


Also, not sure if this info is useful, but heres some info about my system:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13731372

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       12161    66966952+   f  W95 Ext'd (LBA)
/dev/sda5            3825        8923    40957686    7  HPFS/NTFS
/dev/sda6            8924        9063     1124518+  82  Linux swap / Solaris
/dev/sda7            9064       12161    24884653+  83  Linux


(From menu.lst)
title		Windows XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by sethhikari on 2009-09-21
I might not hurt to try from the XP cd command FIXMBR then FIXBOOT and then if you get the XP boot loader you can reinstall grub.

---

### Post by rygar on 2009-09-21
Tried that, but the XP doesn't work :(

As per usual, it spends a lot of time loading stuff, but then instead of giving me the option to press "r" for repair console or install windows, it just goes to a blue screen and tells me there is something wrong with my bios (there is nothing wrong with my bios, ive installed windows before)

i need a method of fixing the xp boot sector from ubuntu, rather than the xp recovery console

---

### Post by sethhikari on 2009-09-21
You don't happen to be using SATA drives are you?

---

### Post by rygar on 2009-09-21
not sure, how do i tell?

---

### Post by sethhikari on 2009-09-21
Guess the easy way is if your drive is connected with the long and very annoying ribbon cable it is IDE but if it has a nice thin ( maybe red ) cable it is SATA.

If in your BIOS the SATA drive is set to AHCI when XP and the XP disks look at your drive you get BSOD!

---

### Post by rygar on 2009-09-24
hmm, no it's not SATA apparently.  I realized now that I'm having sporadic success...  sometimes it launches XP from GRUB and sometimes it gives me the blue screen.  i'm still trying to determine under what conditions XP doesn't boot...

anyway, thanks for your help

---

### Post by Darkwing-Duck on 2009-09-24
Sounds like you need to restore Grub and fix your MBR. Give this a shot and see if it works for you.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

---

### Post by rygar on 2009-09-25
hmm i don't think that's the problem.  if my mbr were messed up, grub wouldn't load, but it does.

---

