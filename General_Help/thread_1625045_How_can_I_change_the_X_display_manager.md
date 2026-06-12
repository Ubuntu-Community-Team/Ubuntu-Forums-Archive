---
title: "How can I change the X display manager?"
date: 2010-11-18
forum: General Help
---

### Post by nolag on 2010-11-18
How can I change the x display manager?  I know that this is only the login screen, and that I am likely nuts for asking, but say I want gnome (or custom since I use compiz?) to be the default session but have the kde login (since it looks nicer).

---

### Post by sanderd17 on 2010-11-18
X is not the login screen, those are completely different things. X is what gnome uses to display it's things, X is the layer between the DE (like gnome kde ...) and the graphical card driver.

to change the login theme: look here: [http://n00bsonubuntu.net/content/how-change-login-screen-ubuntu-1004-lucid-lynx](http://n00bsonubuntu.net/content/how-change-login-screen-ubuntu-1004-lucid-lynx)

---

### Post by ajgreeny on 2010-11-18
> **sanderd17 said:**
> X is not the login screen, those are completely different things. X is what gnome uses to display it's things, X is the layer between the DE (like gnome kde ...) and the graphical card driver.

to change the login theme: look here: [http://n00bsonubuntu.net/content/how-change-login-screen-ubuntu-1004-lucid-lynx](http://n00bsonubuntu.net/content/how-change-login-screen-ubuntu-1004-lucid-lynx)

But if the OP has KDM or XDM installed as well as GDM, he can choose which one to use with ```
sudo dpkg-reconfigure gdm
```
If it is wanted, you can install KDM and use it with the gnome desktop, but be warned, installing it will pull in masses of other KDE applications and libraries.  Only you can tell if it is worth all that to you.

---

### Post by nolag on 2010-11-19
The X system is divided up into parts, I only want the X Display Manager to change.  Can I only get that part and use it?

---

### Post by dino99 on 2010-11-19
yes you can, but reread the 2 latest lines of the previous post :(

maybe you might try something else than ubuntu-desktop, see the other desktops into synaptic

---

