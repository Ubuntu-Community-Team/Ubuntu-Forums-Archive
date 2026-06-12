---
title: "Removing gnome-panel"
date: 2010-10-08
forum: General Help
---

### Post by sneaker12345 on 2010-10-08
I'm trying to remove gnome-panel entirely from my desktop because I only want to have avant running. I tried to search for solutions and only could find the suggestion of removing gnome-panel in gconf-editor under session (see screenshot) and after rebooting the gnome-panel still reloads (it's on the right of my screen). 

Any ideas on how to remove it completely?

---

### Post by sikander3786 on 2010-10-08
Pretty old but it should help.

[http://ubuntuforums.org/showthread.php?t=652367](http://ubuntuforums.org/showthread.php?t=652367)

---

### Post by sneaker12345 on 2010-10-08
Thanks, solved.

---

### Post by sikander3786 on 2010-10-08
Ok. Found these recent ones for you.

[http://ubuntuforums.org/showthread.php?t=1517999&page=1](http://ubuntuforums.org/showthread.php?t=1517999&page=1)

[http://ubuntuforums.org/showthread.php?t=1444461&page=1](http://ubuntuforums.org/showthread.php?t=1444461&page=1)

Different people achieved it in different ways, thats why I posted the links to the thread otherwise I'd have posted the solution actually. See and decide yourself.

---

### Post by xircon on 2010-10-08
All I did was:

```
mv /usr/bin/gnome-panel /usr/bin/gnome-panel-old
```

Then if you need to run it, run gnome-panel-old.

One thing to note is you will lose alt-f2 functionality.  I use lauf attached to the same hotkey.

---

