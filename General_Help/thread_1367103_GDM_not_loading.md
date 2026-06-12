---
title: "GDM not loading"
date: 2009-12-29
forum: General Help
---

### Post by ganeshguru on 2009-12-29
After i booting into the system, i directly taken to the CUI(tty1) mode it is prompting me to type the username and password. Once i logged, i have to type the startx command to start the GDM. I want to avoid this. kindly help me, to boot directly to the GDM login screen

---

### Post by smerral on 2009-12-29
Have you tried re-installing grub?

sudo grub-install /dev/sda

sudo update-grub

---

### Post by VCoolio on 2009-12-29
It could be a setting in grub; else try 'dpkg-reconfigure gdm' and also make sure the file /etc/X11/default-display-manager contains one line that says "/usr/sbin/gdm"

---

### Post by ganeshguru on 2009-12-30
Thanks, it is working now... after changing my /etc/X11/default-display-manager file

---

