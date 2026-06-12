---
title: "Permissions problem"
date: 2012-04-26
forum: General Help
---

### Post by Doug11 on 2012-04-26
Have a little trouble here. I have an SD card with three partitions on it. I need to edit some stuff on it but I need root privileges to do it. I tried to create a root account but I get the "root logins not allowed". It's a big PITA trying to use the terminal to do this copying and pating stuff from one card to another. Is there an easier way to do this. I know on my desktop running 11.10, I can create a root user, but not my laptop using 10.04 LTS. Anyone help me out on this?

---

### Post by westie457 on 2012-04-26
Have you tried running Nautilus with root privileges ```
gksudo nautilus
``` to drag and drop files.

Be careful though as you will have the ability to completely bork your system.

When finished close the window then in terminal Ctrl+C to make sure that Nautilus terminates then close the terminal.

---

### Post by CatKiller on 2012-04-26
In KDE it will be kdesu whatever-the-KDE-file-manager-is-called. (kdesu dolphin, is it?)

---

