---
title: "No keyboard at login prompt"
date: 2009-09-12
forum: General Help
---

### Post by stevebond001 on 2009-09-12
Hi
I booted my PC this morning and got a garbled display, so I rebooted into recovery mode and selected the option to automatically fix graphic errors.
when I next rebooted my keyboard is not recognised so I can't login (if I boot into recovery mode the keyboard works OK)

Does anyone know how to reset my configuration to recognise my keyboard?

Many thanks in advance

Edit
Just found out that if I CTRL-ALT-F2 I can get another (text based) login prompt and my keyboard works OK.  So it must be the graphical interface which is causing the problem

---

### Post by P4man on 2009-09-12
I guess xfix somehow messed up your keyboard.
You can try editing yourself from the terminal by running

```
sudo nano /etc/X11/xorg.conf
```

but tbh, I wouldnt know what to look for or what to change.

---

### Post by stevebond001 on 2009-09-12
Hi
Thanks but the xorg.conf file is virtually empty (just the default entries in it and nothing about the keyboard)

Any other ideas??  I really really don't want to re-install the O/S just for the sake of the keyboard not working when trying to login

---

### Post by P4man on 2009-09-12
Not sure, not on ubuntu here right now, but did you try

```
sudo dpkg-reconfigure xserver-xorg
```
?

---

### Post by stevebond001 on 2009-09-12
P4Man
Thanks for the advice.  ran this and managed to log back in again (although no characters appear when I type ny user mane and password at the login prompt).

Thanks very much

---

