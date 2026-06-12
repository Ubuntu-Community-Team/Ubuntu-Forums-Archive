---
title: "Removing a PC Card"
date: 2010-11-09
forum: General Help
---

### Post by peyre on 2010-11-09
I'm using an old laptop with a PC-Card bay and a cardbus WiFi adapter.  If I remove the WiFi adapter to insert something else in the bay, Lubuntu locks up solid--even the mouse refuses to move.  I assume I'm going about this wrong...is there a proper way to remove the adapter that won't crash the system?

---

### Post by dino99 on 2010-11-09
your system is searching the removed hardware, deselect it into gconf-editor

---

### Post by peyre on 2010-11-09
I don't seem able to do anything with the adapter in gconf-editor, possibly because I'm not running Gnome (see attached).  I can edit little things, like the names of the connections, but I don't see the WiFi adapter hardware in there anyplace.

---

### Post by cavalier911 on 2010-11-09
See **man pccardctl**
Try ```
pccardctl eject 
``` to eject the card in software before you physically remove the card. You may have to use pccardctl info or pccardctl ident to get socket. Then add the socket number to the end of the eject command.

---

### Post by peyre on 2010-11-10
Hey thanks!  That worked great.

---

