---
title: "ndisgtk can't be initialized"
date: 2006-02-19
forum: General Help
---

### Post by gnutux on 2006-02-19
I get this error whenever I try to start ndisgtk:

> 
Failed to load GTK bindings. Please check your Gnome installation.


What should I do??

gnutux

---

### Post by gingermark on 2006-02-20
I don't know the program, but that error means that some of the GTK elements the program relies on aren't there.

How did you install ndisgtk? If you had done it though adept, or with the command line and apt-get then the dependencies should have been taken care of.

Try installing ndiswrapper-utils, python, and python-gnome2 and then see if it works. Apparently they are ndisgtk's dependencies.

---

