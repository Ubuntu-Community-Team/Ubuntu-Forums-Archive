---
title: "Getting a script to run on startup"
date: 2011-10-20
forum: General Help
---

### Post by IBUA on 2011-10-20
Hey!

I've worked out how to get programs to load on start up by creating .desktop files, and currently I've got terminal running on startup.

However, does anyone know how to get a script to load instead of just a program? As so far everything i've tried has failed, with either nothing happened or the terminal opening for half a second then disappearing.

Cheers
IBUA

---

### Post by aeiah on 2011-10-20
lubuntu uses lxde, which uses openbox. the normal openbox method is to add things to ~/.config/openbox/autoshart.sh but lxde has a different place for it (~/.config/lxsession/LXDE/autostart). 

have a look here: [https://wiki.archlinux.org/index.php/LXDE#Autostart_Programs](https://wiki.archlinux.org/index.php/LXDE#Autostart_Programs)

---

### Post by IBUA on 2011-10-20
> **aeiah said:**
> lubuntu uses lxde, which uses openbox. the normal openbox method is to add things to ~/.config/openbox/autoshart.sh but lxde has a different place for it (~/.config/lxsession/LXDE/autostart). 

have a look here: [https://wiki.archlinux.org/index.php/LXDE#Autostart_Programs](https://wiki.archlinux.org/index.php/LXDE#Autostart_Programs)

Awesome! Thank you! Thats seems to work!

Just out of curiosity, would I be able to run a command that works in terminal instead of using the script?

EDIT: In fact it didn't work... I can get programs to load by adding to the .desktop files, but not scripts...

---

### Post by IBUA on 2011-10-20
In fact I had to create a script which ran another script in terminal, and command the first script to run on autoboot.

Thanks anyway!

---

