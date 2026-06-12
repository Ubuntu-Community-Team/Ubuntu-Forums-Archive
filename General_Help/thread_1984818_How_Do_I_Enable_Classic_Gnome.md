---
title: "How Do I Enable Classic Gnome"
date: 2012-05-22
forum: General Help
---

### Post by CarlosinFL on 2012-05-22
Trying Ubuntu out again after a year off. Is there any way I can change back to Ubuntu classic on 12.04? During the Gnome login, I selected 2D but I still have a Unity style dock on the right side of my screen and performance on a quad core machine / 8 GB of RAM is terrible as well. Trying to see if I can make this run better. Also is there a way I can move my window size controls back to the right side of the window rather than the left?

---

### Post by forrestcupp on 2012-05-22
Install gnome-session-fallback, then logout and choose Gnome Classic in the list.

```
sudo apt-get install gnome-session-fallback
```

---

### Post by hal8000 on 2012-05-22
To move the window controls follow this blog:

[http://deviceguru.com/ubuntu-11-10-without-shell-shock/](http://deviceguru.com/ubuntu-11-10-without-shell-shock/)

You need to install gnome-tweak-tool and gconf-editor, but it can be done.


The big difference in 12.04 is that in gnome classic, its not just alt + right click to reconfigure panels.

On my system its  windows-key+alt + right click then you can follow rest of tutorial.

---

