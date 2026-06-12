---
title: "I think I ruined my new computer"
date: 2009-12-16
forum: General Help
---

### Post by cheesefry on 2009-12-16
I just got a new netbook and downloaded a disk to install UNR. It gave me the opportunity for a trial. I tried it out and all went well. I decided to install the OS. Went thru the steps. Almost done when it started giving me errors about needing to reboot due to some partition stuff. I tried 2 more times with the same error. So I decided to reboot as it requested. Now my computer has no OS and gives me a black screen with this:

Check cabel connection..!
PXE-E63: Error while initializing the NIC
PXE-M0F: Exiting intel PXE ROM.
no bootable device -- insert boot disk and press any key.

What do I do??

---

### Post by Muscovy on 2009-12-16
Don't worry, the computer itself isn't ruined.
  I don't know what you did, but it sounds like you booted off when you shouldn't have. Could you explain some of the steps/events in between?

---

### Post by Tclarkie on 2009-12-16
try installingt another os, moblin. your pc is not broken its just crashed during a partition, definitely fixably, try using gparted live

---

### Post by cheesefry on 2009-12-16
Ok, after several restarts, it is now letting me try again. I am at the "prepare disk space" screen. I was last trying to "erase and use entire disk space" Should I do something different??

---

### Post by Muscovy on 2009-12-16
If you don't have any data on there, sure.

---

### Post by cheesefry on 2009-12-16
Ok, it seems to be doing Ok this time. I am excited to give this Linux thing a shot. Love my MAC, hate all past Micosoft computers I've owned. On top of that, Cool people are willing to help out. Thanks guys!

---

### Post by PseudoLemon on 2009-12-16
Erm, Microsoft doesn't make computers...

---

### Post by Chesamo on 2009-12-16
> **PseudoLemon said:**
> Erm, Microsoft doesn't make computers...
True dat. Though I'm sure you know they mean Windows machines rather than Microsoft-brand PCs. ;P

---

### Post by MaxIBoy on 2009-12-17
> **PseudoLemon said:**
> Erm, Microsoft doesn't make computers...
Well then, I guess the Xbox doesn't exist?


To the OP, as others have said it is not a hardware problem. The installation process just screwed up somehow.

If for whatever reason the problem happens again, maybe the ISO got corrupted as part of the download process? The installer disk has an option to check itself for errors; you should run that to see.


Once you get it installed, if you don't like the netbook oriented user interface you can revert it to a more standard user interface.

---

### Post by marshmallow1304 on 2009-12-17
> **cheesefry said:**
> Check cabel connection..!
PXE-E63: Error while initializing the NIC
PXE-M0F: Exiting intel PXE ROM.
no bootable device -- insert boot disk and press any key.

Check the boot order in the BIOS.  It looks like you've got [PXE]("http://en.wikipedia.org/wiki/Preboot_Execution_Environment") before hard drive.

---

### Post by mdshann on 2009-12-18
> **MaxIBoy said:**
> Well then, I guess the Xbox doesn't exist?




Xbox is a game console, but [Surface]("http://www.microsoft.com/surface/Default.aspx") is a computer!

---

### Post by marshmallow1304 on 2009-12-19
> **mdshann said:**
> Xbox is a game console, but [Surface]("http://www.microsoft.com/surface/Default.aspx") is a computer!

But you have to have Silverlight to see it.  I guess I never will.

---

