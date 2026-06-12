---
title: "Can't boot Win7 from grub"
date: 2011-12-31
forum: General Help
---

### Post by marko2012 on 2011-12-31
Help! :confused: I just installed Ubuntu alongside Windows 7. I downloaded and burned ISO to DVD and selected the first option to install alongside Windows 7. After the installation was complete and it rebooted, it takes me straight to Ubuntu and there is no boot menu or option to select Windows 7. I tried pressing Esc during startup but these take me straight back to Ubuntu. I can see all of my windows files are still on the hard drive but I don't know how to get back to/boot up Windows 7. Help!??

---

### Post by 73ckn797 on 2011-12-31
Open a terminal in Ubuntu and enter this command: ```
sudo update-grub
``` enter password when prompted (the screen does not echo your pass word entry) and restart. See how that works.

---

### Post by oldos2er on 2011-12-31
Moved to separate thread.

---

### Post by vpharry on 2011-12-31
> **73ckn797 said:**
> Open a terminal in Ubuntu and enter this command: ```
sudo update-grub
``` enter password when prompted (the screen does not echo your pass word entry) and restart. See how that works.
Ya.. that should solve the problem... :P It had happened to me once... otherwise u can try to reinstall grub:P

---

