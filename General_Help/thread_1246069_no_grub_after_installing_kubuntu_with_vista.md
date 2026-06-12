---
title: "no grub after installing kubuntu with vista"
date: 2009-08-21
forum: General Help
---

### Post by spedax on 2009-08-21
I installed vista first. It booted fine.
Then I installed kubuntu on a second partition on the hd.

after rebooting the system it doesnt show grub but just boots my vista.

I tried doing [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
But this didnt seem to fix the problem, its just does the same as before ( boot vista without showing a bootloader )

any suggestions would be greatly appriciated!

---

### Post by realzippy on 2009-08-21
download Supergrubdisc and let it fix your GRUB...

[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

---

### Post by jacksaff on 2009-08-21
If kubuntu installed ok, this shouldn't happen. This isn't an ubuntu thing - installing grub properly has been pretty much a given on any general purpose distribution for several years.
Did you install grub to mbr (default)?
If kubuntu installed fine then windows won't have even started to load when the grub screen comes up.

Try installing kubuntu again (it's only 10 minutes), make sure you don't override the option to install grub to mbr, and make sure it's not giving any errors.

---

### Post by spedax on 2009-08-21
I think Kubuntu installed fine, installed over 3 times now and is still have the same problem, anyway can I see whats actually installed on my MBR? then I post it here so someone might see what the problem is?

---

