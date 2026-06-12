---
title: "ice-wm-ubuntu"
date: 2006-02-08
forum: General Help
---

### Post by Ubuntuud on 2006-02-08
Hi, I have a laptop and I want to make the battery last longer. Currently I'm running gnome, but is it possible to install icewm as the _only_ window manager during installation? And will it preserve a lot of power, or is there an other, more power efficient wm? Thanks in advance...

---

### Post by az on 2006-02-08
[QUOTE=Ubuntuud]but is it possible to install icewm as the _only_ window manager during installation? ...[/QUOTE]

Install in server mode (type server at the prompt and hit enter)

Then, when everything is installed and you log in, type

sudo nano /etc/apt/sources.list
and uncomment the universe repository line.

sudo apt-get update

sudo apt-get install x-window-system-core gdm icewm synaptic xterm

When you boot, you will have to change the default session to icewm, as it will try to use a gnome session.  Other than that, run synaptic and install whatever else you need.




[QUOTE=Ubuntuud]And will it preserve a lot of power, ...[/QUOTE]

I doubt it.

---

### Post by Ubuntuud on 2006-02-08
So the power usage isn't related to the wm?

---

### Post by Ubuntuud on 2006-02-08
And is it (I'm almost sure it is) possible to do the same with enlightenment_17_?

---

