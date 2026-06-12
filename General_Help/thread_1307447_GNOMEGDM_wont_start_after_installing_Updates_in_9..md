---
title: "GNOME/GDM wont start after installing Updates in 9.10"
date: 2009-10-31
forum: General Help
---

### Post by LostOverThere on 2009-10-31
Hello,

Today after completing a fresh install with Ubuntu 9.10, and installing updates via the upgrade manager, my system will no longer boot.

It appears there is a problem with GDM or GNOME in General. When it boots, after the white Ubuntu logo disappears, the screen starts flashing on and off with the console. The words "login" appear on screen, asking me to login. I can't type in there though.

Typing *startx* does nothing.

Thanks in Advance.

---

### Post by misfitpierce on 2009-10-31
What video card are you using on your computer to start this off... May have something to do with it.

---

### Post by LostOverThere on 2009-10-31
I'm using a Geforce 4 MX. I don't believe the problem lies within the graphics card/drive, as after updating the driver, I could boot just fine.

---

### Post by LostOverThere on 2009-10-31
Running 'startx' gives me a heap of errors, similar to this:

[I]
Saw signal 11. Server aborting
ddxsiggiveup: re-raising 11
xinit: no such process (errno 3) server error.[/I]

---

### Post by jose_maria0 on 2009-10-31
The same thing is happening to me. I am using an nVidia Graphics card. The only difference is that after typing startx, I get no errors and I really start Xorg.

---

