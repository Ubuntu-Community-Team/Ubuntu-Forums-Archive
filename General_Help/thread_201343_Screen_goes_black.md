---
title: "Screen goes black"
date: 2006-06-21
forum: General Help
---

### Post by Aardfox on 2006-06-21
When I start Ubuntu with the live cd (the 1386 and the amd64 version) and it gets to the desktop the screen goes black every time.
I am using an ATI Radeon x700.
Since I'm booting with the live cd I assume there's no way I could install some radeon drivers first so...
Should I use the server version?
If I do, how do I install the drivers from a cd while at the command prompt?

---

### Post by eth on 2006-06-21
when the screen goes black, type

**ctrl+alt+F1**

you'll be taken in a console. from there

```
vim /etc/X11/xorg.conf
```

search for **"ati"** string in section **Device** and replace it with **vesa**

it's just a poor poor poor solution to get the things going, once you have a desktop viewable and you decide to install the OS, you can think about getting a real fglrx driver and 3D acc working

---

### Post by Aardfox on 2006-06-21
I did all that sucessfully but then I realized I don't know how to get back to the GUI.
How do I do that? Thanks.

---

### Post by Daniel Ibrahim on 2006-06-21
No Problem, just click Alt+F7
(there are several Terminals on F1 until F6, in Unix or Linuxes F5 or F7 are the graphical UI)

---

### Post by Aardfox on 2006-06-21
Thanks so much for your quick reply :)

---

