---
title: "Edit Menus not working"
date: 2009-12-30
forum: General Help
---

### Post by tomos on 2009-12-30
Using Karmic.

Right-clicking the Applications menu followed by left-clicking "Edit menus" does nothing.  Also, System>Preferences>Main Menu gives nothing.

On the command line I entered
 
# sudo alacarte 

and the menus appeared for editing.


thanks
tomos

---

### Post by dcstar on 2009-12-31
> **tomos said:**
> Using Karmic.

Right-clicking the Applications menu followed by left-clicking "Edit menus" does nothing.  Also, System>Preferences>Main Menu gives nothing.

On the command line I entered
 
# **sudo alacarte** 

and the menus appeared for editing.


This is **not** a sudo run application, it is meant to change the user settings (assuming the user has rights to use it).

---

### Post by SabreWolfy on 2010-05-20
"Edit Menus" broken in Lucid.

---

### Post by WorMzy on 2010-05-20
Not for me it isn't.

---

### Post by ubunterooster on 2010-05-20
> **dcstar said:**
> This is **not** a sudo run application, it is meant to change the user settings (assuming the user has rights to use it).
Meaning just run ```
alacarte
``` without the sudo prefix. If this does not work the problem is with permissions

And I have had problems with that also.

---

### Post by SabreWolfy on 2010-05-20
Check file permissions on ~/.config/menus

Running 'sudo alacarte' will change permissions on this folder to root. Changing them back to user and then running alacarte launched the program for me. The "Edit Menus" selection is still not working in Lucid though.

---

### Post by SabreWolfy on 2010-05-21
"alacarte" and "Edit Menus" are both working as expected for me in Karmic and Lucdid.

---

