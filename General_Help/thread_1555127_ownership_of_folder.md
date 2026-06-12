---
title: "ownership of folder"
date: 2010-08-17
forum: General Help
---

### Post by kree8or on 2010-08-17
Hi, I've just installed LAMP and when I try to save a file in var/www/ i get a error message saying "Error moving file: Permission denied". When I go to the permission page on the folder options, i cant change anything because it belongs to root. So, i open a termnial and use "su" to change to root, but it still wont allow me to change anything (everything is greyed out) on the folder options. Please help!
Thanks 
Kree

---

### Post by earthpigg on 2010-08-17
hi,

once you get to the root terminal, you will only have root access for things done *in or from that root terminal*.

start dolphin or your file manager of choice *from the root terminal* and try it there. i would assume starting dolphin from the root terminal is as easy as typing 'dolphin', but i've never used kubuntu so don't know for certain.

if it still isn't working, it may be a dolphin issue that could be resolved by using an alternative file manager. as i said, i've never used dolphin so do not know. i do know, however, that pcmanfm has outstanding graphical permissions editing (if you don't mind a gtk app being installed).

---

