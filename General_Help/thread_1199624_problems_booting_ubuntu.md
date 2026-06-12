---
title: "problems booting ubuntu"
date: 2009-06-29
forum: General Help
---

### Post by mittparadox on 2009-06-29
first of im new to this forum so hi [U]):P
[/U]
yesterday i used wubi to install ubuntu and everything was working good. atleast it looked like it^^ 
today i tryed to turn on visual effects and couldent turn it on. i notised my ati drivers  where not enabled 
(there was a warning abouth them not being open source or whatever) so i enabled them and restarted. now i cant boot :( i just get:

```
[Firmware Bug]: Powernow-k8: Your BIOS does not provide ACPI_PPS objects in a way that linux understands. 
Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
```then i get the login stuff at the bottom and so i log in and nothings happening :S
i can type stuff but i dont realy know what to type :D
any idea what to do?

My pc:
Motherboard: M3a32 MVP Deluxe
CPU: AMD Phenom X4 Black Edition 9850
GFX card's: 2x HIS Radeon HD 4850
RAM: 8GB Corsair Dominator

---

### Post by paul_be on 2009-06-29
login then type **startx** and see if the gui loads

---

### Post by kokkus on 2009-06-29
Type startx. And you you have to disable the graphic card.
Reboot your PC, and in grub you choose Recovery Mode.
When the menu comes up, choose "try to fix graphic settings" or whatever it says. Then you can boot ubuntu again.
The problem is your ATI graphic card.
Most ATI cards are not supported by Ubuntu, so I would recommend you to buy another one, like NVidia.

---

### Post by mittparadox on 2009-06-29
that dident work.
i just got this: [IMG]http://img8.imageshack.us/img8/1104/bilde0018.jpg[/IMG]

---

### Post by mittparadox on 2009-06-29
bump

---

