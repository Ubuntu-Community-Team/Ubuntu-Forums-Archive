---
title: "new kernel not automatically added to boot list"
date: 2009-08-19
forum: General Help
---

### Post by Post Monkeh on 2009-08-19
i downloaded and installed an update earlier for the kernel (2.6.28-15) through automatic updates.

any other time the kernel has updated, my grub list updated automatically, however this time when i rebooted, i was still just left with 2.6.28-14 as my most recent option.


one thing is, after the "local access = root access" thread the other day, i folowed some links to secure my laptop a bit more and locked the grub list, the recovery modes, and removed the ability for normal users to see the menu.lst file. root obviously still has full read/write access.


i have a config-2.6.28-15-generic and an abi-2.6.28-15-generic in my boot folder, so the kernel update HAS been installed, would my messing with the file permissions for my menu.lst have prevented it from being updated?

one further thing, before i rebooted after the update, i went to edit the menu.lst to lock the new recovery option, but obviously it wasn't there.  could me accessing the menu.lst file (i used gedit btw) prior to my reboot have been what caused this?

---

### Post by drs305 on 2009-08-19
Yes, the grub settings can effect whether or not a new kernel is used after installation.

I recommend StartUp-Manager, a GUI app for tweaking menu.lst. Check this link for a guide to installing SUM and an explanation of the options. There are also explanations on what some of the menu.lst options do if you want to edit menu.lst manually.

[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Post Monkeh on 2009-08-19
sorted now. i followed your link and did a sudo update-grub aftetr a reboot and that added the new kernel.

i use startup manager, i never realised it could lock the older kernels and rescue selections.  i'll just use it from now on.  
cheers.

---

