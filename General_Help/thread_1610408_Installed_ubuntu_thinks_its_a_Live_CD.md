---
title: "Installed ubuntu thinks its a Live CD?"
date: 2010-10-31
forum: General Help
---

### Post by complience on 2010-10-31
I've installed ubuntu 10.10 but after the BIOS boots the Hard drive I see the following message.

Loading Operating system...
boot from CD/DVD ROM...

(there is no CD loaded in the drive)
Why is ubuntu trying to boot from a CD?

My ubuntu installation then starts up as normal.. so its not a big problem, but it is annoying.

System Specs
AMD Phenom II X4 955 Black Edition Socket AM3 3.2 GHz 8MB L3 Cache Processor

ASUS M4A79T Deluxe 790FX Socket AM3 DDR3 8 channel audio ATX Motherboard

OCZ 4GB (2x2GB) DDR3 1333MHz/PC3-10666 Gold i5 Memory Kit 1.65V CL9(9-9-9-20)

---

### Post by PRC09 on 2010-10-31
You need to enter the bios of the computer and change the boot order of your drives.Just select the hard drive instead of the cd rom drive.

---

### Post by cpmman on 2010-10-31
When you switch on the BIOS controls where it will boot from.  You can alter the boot order by interrupting the BIOS with usually a function key (F2 or F10 or similar) or sometimes the Esc key.  It will present some menus where you may change the boot order (make the hard disc the first option for example).  This will stop it from looking for an operating system on the cd.  It is not ubuntu doing this - ubuntu is not part of the process until it is loaded from the disc.

---

### Post by Verbeck on 2010-10-31
its not the os, its your bios boot order settings (most probably) . try changing that

---

### Post by coffeecat on 2010-10-31
> **complience said:**
> but it is annoying.

Really? I find it reassuring. I know that my BIOS is set to boot from the optical drive first when I see this so that I don't have to fiddle with the BIOS if I need to boot with a live CD to do some repair/maintenance work.

The loading from CD message lasts all of - ooh, let me see - half a second.

---

