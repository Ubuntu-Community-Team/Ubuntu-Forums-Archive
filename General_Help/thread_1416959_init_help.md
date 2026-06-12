---
title: "init help"
date: 2010-02-26
forum: General Help
---

### Post by Thinice16 on 2010-02-26
what is the runlevel so i can start up in the terminal and use startx if i need to use x?

---

### Post by Brandon Williams on 2010-02-27
In debian based systems, the run level for X and console logins is the same, unlike most other *nix platforms. If you don't want to use a graphical login manager, use sudo to edit /etc/X11/default-display-manager and remove all its content. If that file is empty, then no graphical login manager will be started on boot and you'll just get a console login prompt.

---

