---
title: "How to get auto gnome login ?"
date: 2011-10-15
forum: General Help
---

### Post by nesa24 on 2011-10-15
Hello
i need help to set autologin to gnome on every login.
How can i do that ?
Best regards

[IMG]http://www.liberiangeek.net/wp-content/uploads/2011/08/Return-to-Ubuntu-Classic-Desktop-in-U.10_13AB6/gnome_fallback_2.png[/IMG]

---

### Post by Frogs Hair on 2011-10-15
Hello and Welcome

What version of Ubuntu ? With 11.10 the automatic login setting under user accounts , and with older versions it was under login settings .

---

### Post by nesa24 on 2011-10-15
> **Frogs Hair said:**
> Hello and Welcome

What version of Ubuntu ? With 11.10 the automatic login setting under user accounts , and with older versions it was under login settings .

11.10 * updated from 11.04
Dont have selection of session in User Accounts

---

### Post by flipper T on 2011-10-15
ensure that you have auto log in enabled in system settings / user accounts, then enter this in a terminal:

sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell

---

### Post by nesa24 on 2011-10-15
> **flipper T said:**
> ensure that you have auto log in enabled in system settings / user accounts, then enter this in a terminal:

sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell

Worked!
Any shortcut for no effect gnome shell ?

---

