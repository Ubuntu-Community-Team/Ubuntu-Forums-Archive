---
title: "error: unkown command 'drivemap'"
date: 2010-12-16
forum: General Help
---

### Post by nemo004 on 2010-12-16
hello, i'm completely new Ubuntu. i recently downloaded wubi and attempted to install ubuntu. everything went smoothly and the first time i tried to boot up ubuntu, the purple desktop background came up and ubuntu finished its installation. then i had to select which operating system to use (XP or newly Ubuntu), and when i choose ubuntu i get the following message:

"Choose an operating system to boot from:
[XP is the only OS listed]

Use the up and down keys to select which entry is highlighted. Press enter to boot the selected OS. 'e' to edit the commands before booting or 'c' for a command-line. ESC to return to previous menu."

after i select XP, the error message "error: unkown command 'drivemap'." displays briefly in the upper left hand corner. Any advice on what to do? I am currently running Windows XP. thanks!

---

### Post by bcbc on 2010-12-16
Did you click on the SKIP button during the install (while the slideshow was playing?). If you did, then a major part of the Wubi install was not installed and you cannot boot it. The only fix is to reinstall.

If you reinstall Wubi using the version from ubuntu.com - then the first time Update Manager runs it will prompt you to update packages grub-pc and grub-common. They will be far down in the list under the "Recommended" updates section. Do not update these packages or they will break the Wubi install - so make sure you uncheck these.

---

