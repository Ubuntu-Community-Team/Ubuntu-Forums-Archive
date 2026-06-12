---
title: "Dual boot problems"
date: 2011-09-05
forum: General Help
---

### Post by Frodo0321 on 2011-09-05
How do you switch between ubuntu and vista?

---

### Post by Duncan Williams on 2011-09-05
hold the shift key down whilst booting, this should bring up `grub'.

---

### Post by Frodo0321 on 2011-09-05
Tried that and still nothing. After my computer boots up instead of normally starting, it goes into a kind of sleep mode and the monitor reads "signal out of range" for about 20 seconds before ubuntu runs

---

### Post by Duncan Williams on 2011-09-05
try supergrub-2 (create boot cd, boot with it, this may also fix things)

[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

---

### Post by Gwaro on 2011-09-05
You can try using grub-customizer.
[http://www.liberiangeek.net/2011/02/customize-ubuntu-grub-boot-menu-grub-customizer/](http://www.liberiangeek.net/2011/02/customize-ubuntu-grub-boot-menu-grub-customizer/)

---

### Post by Mark Phelps on 2011-09-05
If you're saying that there is no Vista entry in the GRUB menu, you add one by opening a terminal in Ubuntu and entering "sudo update-grub".  Watch closely as it enumerates the kernels and OSs it finds -- and you should see a line containing something like "Windows Vista Loader on (xxx)".

The next time you boot after that, you should see a GRUB menu with entries for Ubuntu and Vista.

---

