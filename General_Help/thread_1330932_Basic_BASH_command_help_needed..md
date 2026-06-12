---
title: "Basic BASH command help needed."
date: 2009-11-18
forum: General Help
---

### Post by Cityscape on 2009-11-18
I'm sorry, it's been awhile since I've used the Linux command line.  I if was to copy "example.so" from "/home/programs" to "/usr/lib/purple-2/" what command do I need? Or is there a way I can do this without using Terminal?

---

### Post by scragar on 2009-11-18
```
sudo cp /home/programs/example.so /usr/lib/purple-2/
```
You could also do it graphically by lauching a terminal with root perms.
```
gksu nautilus
```replacing nautilus with **thunar** for Xubuntu users.

---

