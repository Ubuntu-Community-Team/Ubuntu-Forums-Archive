---
title: "Brightness control"
date: 2012-05-05
forum: General Help
---

### Post by MibunoOokami on 2012-05-05
Hi everyone, I just bought a new netbook (HP mini 110) and installed Ubuntu 12.04 32bit onto it but for some reason the brightness controls don't do anything. I used the original OS to start with to check out all the features before deleting windoze and installing Ubuntu. I've installed 12.04 successfully on another laptop without it affecting the brightness controls.

Can anyone offer any suggestions?

---

### Post by MibunoOokami on 2012-05-09
I've tried changing a line in grub to say 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

then 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=linux"

and finally

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor and acpi_osi=linux"

I updated grub each time as well, but none of these have worked. Any suggestions will be greatly appreciated. Forgot to say, I've tried the liveCD for both 32 and 64bit but it didn't help.

---

### Post by MibunoOokami on 2012-08-21
This thread has been solved over here [http://ubuntuforums.org/showthread.php?t=2039350](http://ubuntuforums.org/showthread.php?t=2039350) thanks.

---

