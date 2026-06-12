---
title: "help booting from cd"
date: 2010-04-22
forum: General Help
---

### Post by tc47274 on 2010-04-22
I have been messing with ubuntu for awhile but find it too confusing in some areas for me. How do I reinstall windows? i tried booting from the windows disk and i see no option to boot from the cd other than the bios but ubuntu doesn't seem to offer this option. can ab
ny one help. thanks.

---

### Post by ajgreeny on 2010-04-22
You set the bios long before you have booted into ubuntu!

Put the CD into the drive and reboot the computer.  There should be a key-press prompt shown on screen to enter bios or setup, and from there you will need to set the CD as first boot device.

I do wonder, however, whether you installed ubuntu inside windows, using wubi.  If so, you need to uninstall it from the windows control-panel ->Add/Remove utility, and you may also need to edit the boot.ini file at the root of your C: drive and remove any reference to ubuntu from that.

---

