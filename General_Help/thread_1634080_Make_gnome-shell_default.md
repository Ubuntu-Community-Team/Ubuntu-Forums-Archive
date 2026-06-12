---
title: "Make gnome-shell default"
date: 2010-11-30
forum: General Help
---

### Post by conradin on 2010-11-30
Hey all, 
I want to make gnome shell my default window manager. I have it installed, and can get it to run from the terminal with gnome-shell --replace. 
the effects aren't permanent though. I tried setting gnome-shell to be a start up application but this hasn't worked. I dont want to remove compiz or metacity before knowing if I can get gnome-shell to run by default somehow. 

So, how can I get gnome-shell to be my default windows manager?

---

### Post by Harry33 on 2010-11-30
So I assume you have installed gnome-shell from official repos or Ricotz PPA.
In that case you need to install (from repos) package gnome3-session.
Then reboot and at login window (from the bottom panel) choose session "Gnome3" instead of "Ubuntu Desktop Environment".
After this the G-S is default until you choose otherwise from the login window.

---

### Post by conradin on 2010-12-01
Sweet, Totally worked!

---

