---
title: "How can I make grub show the boot menu everytime and not with shift?"
date: 2010-08-29
forum: General Help
---

### Post by ZequeZ on 2010-08-29
Well, that, my grub boot menu only show up if I hold the shift key, I want it every time. How can I archive this?

Sorry for my english :P

---

### Post by kerry_s on 2010-08-29
press-> alt+f2
type-> gksudo gedit /etc/default/grub

comment out(#) "GRUB_HIDDEN_TIMEOUT=0"
you might want to set "GRUB_TIMEOUT=10" to like 3 or 5
close it after your done

in accessories-> terminal, run "sudo update-grub"

reboot & check it out

---

### Post by jimbop99 on 2010-08-29
you can also install startup manager form the software center and change it in there.

---

