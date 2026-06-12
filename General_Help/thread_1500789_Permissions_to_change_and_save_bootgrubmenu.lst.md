---
title: "Permissions to change and save /boot/grub/menu.lst"
date: 2010-06-03
forum: General Help
---

### Post by oldtraveler on 2010-06-03
[color=red]SOLVED[/color]
I have several Ubuntu OS, but I always install 9.04 last so that I can get Grub Legacy which works better with my Windows 7 64 bit than Grub 2.  I wish to edit and save /boot/grub/menu.lst  on the 9.04 OS.  When I attempt to do this I get an error stating that I do not have the permissions necessary to do so.  How may I obtain the permission?

---

### Post by cariboo on 2010-06-03
You need to be root to edit files not in your home directory. You can use sudo for command line programs and gksu for graphical applications. To edit /boot/grub/menu.lst, press Alt-F2 and type:

```
gksu gedit /boot/grub/menu.lst
```

---

### Post by oldtraveler on 2010-06-03
Thank you that works.  Easy when you know how.

---

