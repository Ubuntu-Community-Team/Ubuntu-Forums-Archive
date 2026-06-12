---
title: "Xdialog on Maverick"
date: 2011-01-21
forum: General Help
---

### Post by jeferod83 on 2011-01-21
I have a HP laptop, and recently I configured the Remote Control to control the sound, and make a funny joke when a curious friend press the Power button in the remote control.
To make this work, I want to make a shell script that calls a dialog, not a console dialog, but a GTK dialog.
Then I tried to install the package "xdialog", that is no longer present on the official repositories, and I tried to find a similar package, but no success. What comes closest is "dialog", but this shows only a console dialog.

Anyone have an idea, or knows other package that makes this job?

Tks

---

### Post by kerry_s on 2011-01-21
ubuntu has zenity. use "man zenity" in the terminal to learn more.

example:
zenity --info --text="self destruct activated"

---

### Post by jeferod83 on 2011-01-21
that is it! tks kerry

---

