---
title: "Can not add indicator-applets on gnome-panel after installing it from source.(11.04)"
date: 2012-05-18
forum: General Help
---

### Post by sunny_sigara on 2012-05-18
I was trying to fix a bug ([https://bugzilla.gnome.org/show_bug.cgi?id=633566](https://bugzilla.gnome.org/show_bug.cgi?id=633566)) with gnome-panel on ubuntu natty.These are the steps i performed.

1) sudo apt-get source gnome-panel
2) sudo apt-get build-dep gnome-panel
3) patch the required file, then
4) ./configure
5) sudo make
6) sudo make install.

At this point the bug is fixed, but i couldn't  see any ubuntu indicators(indicator-session, indicator-me, indicator-appmenu-complete...etc) on add-to-panel window. Also with system-monitor i couldn't see any indicator service running.

I tried to remove the indicators & re-install it from synaptic. But that didn't help.What i am missing?Please help.

---

### Post by sunny_sigara on 2012-05-20
bump!

---

