---
title: "Windows won't boot after cmos/bios reset but Ubuntu will"
date: 2009-09-24
forum: General Help
---

### Post by Primefalcon on 2009-09-24
I recently reset my cmos and bios everything went fine, but after it Windows won't boot, I duel boot windows with Ubuntu and ubuntu still works 100% ok but windows wont boot just brings me to a screen asking me for safe, cli or last known config, however regardless of which I choose the computer just restarts, however if I choose ubuntu at the grub prompt it boots normally everything 100% ok, anyone know what's going on here?

---

### Post by Primefalcon on 2009-09-24
I'd like to try and find a solution to this bar reformatting

---

### Post by bobince on 2009-09-24
Try toggling the ACPI setting in your BIOS. WinXP will only boot with the setting it had when you installed the OS; Linux will boot with any setting. So if a CMOS reset changes the ACPI setting it is possible for WinXP to break.

---

### Post by Primefalcon on 2009-09-24
I can't even find an acpi setting in the bios, for reference the system I'm using is a dell dimension e520

---

### Post by turbostd on 2009-09-24
try the sata settings. It sounds like it got switched from compatability mode to ahci or the other way around.

---

### Post by Primefalcon on 2009-09-24
I also can't find a setting for ahci

there's this

SATA Operation
RAID Autodetect/ATA or RAID On

changing it to the first option makes the computer unbootable it needs to be set to raid on. That's the only sata style mode setting I can find in there

---

### Post by turbostd on 2009-09-24
Im not too familure with the bios in dells wish i had one here too look at so i could help you out. What model is it? Im pretty shure that is the option that needs fixed so windows will boot i just dont know where it is in the bios.

---

### Post by Primefalcon on 2009-09-24
> **turbostd said:**
> Im not too familure with the bios in dells wish i had one here too look at so i could help you out. What model is it? Im pretty shure that is the option that needs fixed so windows will boot i just dont know where it is in the bios.

Its a dimension e520, and I do appreciate all the help you've given so far as well thank you

---

### Post by Primefalcon on 2009-09-25
Ok I seem to have the problem solved now, weird thing is I added in  a slave drive to this computer, and disabled fast boot and re-enabled the RAID Autodetect/ATA which strangely it accepted this time. But anyhow now everything is working fine, thanks for your help you really did help me with where to look.

TB I wish I could just throw windows in the trash as an Operating system the Windows branch are horrible, I;'ve been using ubuntu for quite a few years now and I it keeps getting better and better

---

