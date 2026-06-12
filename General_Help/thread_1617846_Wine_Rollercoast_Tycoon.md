---
title: "Wine Rollercoast Tycoon"
date: 2010-11-09
forum: General Help
---

### Post by kirkface8 on 2010-11-09
At this point in time i am attempting to install Roller-coaster tycoon through wine. Winehq states that it should work fine. with gold silver and bronze ratings on different versions.

I mount the iso run the seteup.exe click install and the error "Error determining size of file H:\RollerCoaster_Tycoon_iso\Saved Games\001" pops up.
Does anyone know how to resolve this?

Thanks
Kirkface8

---

### Post by kirkface8 on 2010-11-09
Solved. Furios Iso mount seemed to be casuing the problem. Mounting the iso through terminal using 
```
 
sudo mount -o loop /directory/for/rollercoastertycoon.iso /media 
```

Solved this problem

---

