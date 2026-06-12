---
title: "No MBR"
date: 2009-07-06
forum: General Help
---

### Post by Monotoko on 2009-07-06
i sorta need to fix my Windows XP MBR as i kinda screwed up ubuntu. What i need to do is get into XP, so i can make another ubuntu disk and then reinstall ubuntu (i misplaced my LiveCD) i thought it would be easy enough to do.

My problem however, is that XP will not let me into its repair console, whenever i put the disk in, it takes me straight to the installation page, where i choose what drive i want to install on, rather than giving me the "Welcome to setup" and letting me press R to repair.

---

### Post by Monotoko on 2009-07-06
anyone?

---

### Post by JC Cheloven on 2009-07-06
Can't help in the windoze bit; seems strange (perhaps you're using an OEM recovery version instead of a true xp disk?).

I think you'd better to look for your ubuntu cd. After reinstalation, you'll be able to boot also xp from grub menu.

---

### Post by Monotoko on 2009-07-06
Nahh its a proper XP CD....i shall maybe try a Windoze forum somewhere.

Its annoying me the fact that i have misplaced my LiveCD....the computer im on at the moment doesnt have a disk drive either....but it does have USB...is there any way i could use a LiveUSB?

---

### Post by mhgsys on 2009-07-06
Well, I guess in this  case you have a recovery windows disk, and not the "full" disk, which means the recovery option will not be available from that cd.

I suggest you use another windows disk, and not a recovery disk.

Anyway; 
If you can't obtain another cd you might wanna try this;

[http://support.microsoft.com/default.aspx?scid=kb;en-us;q310994](http://support.microsoft.com/default.aspx?scid=kb;en-us;q310994)

Yuk!~
:lolflag:

edit: oHw, ... did you just say it doesn't  have a floppy drive? d*mn.
btw, I can't believe MS is serious suggesting  using 6 floppy's !!

---

### Post by mhgsys on 2009-07-06
> **Monotoko said:**
> Nahh its a proper XP CD....i shall maybe try a Windoze forum somewhere.

Its annoying me the fact that i have misplaced my LiveCD....the computer im on at the moment doesnt have a disk drive either....but it does have USB...is there any way i could use a LiveUSB?

Well, you could.
But since your already on another computer, why don't you just download ubuntu and burn a new cd , or create  a bootable usb from the .iso

---

### Post by ajgreeny on 2009-07-06
Or download supergrub which will repair your MBR and then you can sort out another copy of ubuntu.  Supergrub is a much smaller download than ubuntu.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by piratebill on 2009-07-06
get a windows 98 boot disk.  At prompt type

```
fdisk /mbr
```

---

### Post by Monotoko on 2009-07-06
> **mhgsys said:**
> Well, you could.
But since your already on another computer, why don't you just download ubuntu and burn a new cd , or create  a bootable usb from the .iso

It has no disk drive :P

But i managed to get a LiveUSB device and use that :)

---

