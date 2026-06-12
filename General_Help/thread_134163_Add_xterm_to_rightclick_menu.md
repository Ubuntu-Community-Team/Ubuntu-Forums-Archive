---
title: "Add xterm to rightclick menu?"
date: 2006-02-21
forum: General Help
---

### Post by bigblop on 2006-02-21
Is there someway to add xterm or gnome-terminal to the menu I get when I right click with the mouse?

---

### Post by kaamos on 2006-02-21
Yep.
```
sudo apt-get install nautilus-open-terminal
```
It uses gnome-terminal, but I guess there could be a way to make it open up xterm instead.

Nautilus actions is another choice.

---

### Post by bigblop on 2006-02-21
Just installed nautilus-open-terminal, but I still cannot choose to open a gnome-terminal when i right click on the desktop in gnome

---

### Post by kaamos on 2006-02-21
Hmm, maybe you have to log out/in. Or do "killall nautilus".

---

### Post by dcstar on 2006-02-21
[QUOTE=bigblop]Is there someway to add xterm or gnome-terminal to the menu I get when I right click with the mouse?[/QUOTE]
It is possible to add a "Scripts" menu that is visible on Right-click, and then you can put basically anything you like (as a script) in that space.

Do a forum search for for adding gnome scripts, I seem to remember a HOWTO somewhere.

---

