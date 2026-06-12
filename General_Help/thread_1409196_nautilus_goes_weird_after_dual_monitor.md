---
title: "nautilus goes weird after dual monitor"
date: 2010-02-17
forum: General Help
---

### Post by garuhhh on 2010-02-17
hi! am having this weird problem with nautilus. it is sometimes triggered when i activate dual monitor (i'm using nvidia-settings). Actually the entire computer seemingly changes its theme, but after simply running System > Appearance, all goes back to normal except for nautilus (that includes icons in the desktop). please see attached image.

Logging out then logging back in solves the problem, but i don't want to log out just to correct the problem. Is there anything i need to restart to bring it back to normal?

i've tried "compiz --replace" and "compiz --restart" and even "metacity --replace" but it doesn't do anything

thanks for any help! 

by the way, i'm using ubuntu 9.10 64bits, using the default theme, nvidia driver (the default which comes with ubuntu 9.10),using compiz.. tell me what details i need to give.. thanks!

---

### Post by garuhhh on 2010-02-18
turning off compiz also doesn't help :(

---

### Post by garuhhh on 2010-03-11
ideas anyone?

---

### Post by flippo on 2010-03-11
What is your default window manager?
To figure this out run gconf-editor (open a terminal and type gconf-editor)
/ -> desktop -> gnome -> session -> required_componenets -> windowmanager

---

### Post by garuhhh on 2010-03-11
it says compiz.

---

### Post by garuhhh on 2010-03-17
anymore ideas? :(

---

### Post by garuhhh on 2010-04-04
if i do "gksu nautilus" nautilus works well, like what you see in the attached image..

any ideas please?

---

