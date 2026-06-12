---
title: "Toshiba Laptop, unable to run ubuntu install"
date: 2010-12-09
forum: General Help
---

### Post by sr_guy on 2010-12-09
I have an older Toshiba A65-S1067. It only has 256MB ram, but I will be upgrading that next week to 1.2GB. For some reason I cannot get the ubuntu setup to run on the install cd no matter what distro I try (9.04, 10.04, 10.10 32bit).

I boot up, press c, so that the bios to detect a bootable cd, I see the ubuntu logo for about 15 sec, and then the screen goes black, and hear random cd spinups that go on for 15min, but with no install screen.

I've tried these options on the install menu:

Both:

F4 = Safegraphics selected
F6 = "acpi=off" "noapic" and "nolapic" all checked


I was able to get Fedora 8.0 with gnome installed, but I prefer ubuntu. Any ideas/help would be appreciated.

---

### Post by morningsmith on 2010-12-09
Do you have a USB stick and the option to boot from thumb drive? I just installed Ubuntu 10.04 on my newer Toshiba using the USB install and it went flawlessly.

---

### Post by wojox on 2010-12-09
Do you know your graphics card? Try F6 "nomodeset" as your only option.

---

### Post by sr_guy on 2010-12-10
So, acpi=off by itself worked. 


Now... how do I configure remastersys to backup my laptop and have the acpi=off option in the install boot menu?

---

