---
title: "Where does Arora look for Flash plugin?"
date: 2010-02-26
forum: General Help
---

### Post by Mustache Villain on 2010-02-26
I've installed Flash plugin the unconventional way and made a **plugins** directory in **~/.mozilla** and copied the **libflashplayer.so** to it. This works fine for Firefox, but not for Arora. I was wondering in what directory Arora looks for the Flash plugin? Should I also symbolic link to a directory in /usr/lib? What are the common directories Adobe Flash gets installed in?

---

### Post by Mustache Villain on 2010-02-26
I found it by experimenting with different directories apparently Arora looks at the following directory for the Adobe Flash "libflashplayer.so" plugin file:

> /usr/lib/flashplugin-installerSo I just created a symbolic link to that directory from the ~/.mozilla/plugins/ directory:

```
sudo ln -s ~/.mozilla/plugins/libflashplayer.so /usr/lib/flashplugin-installer/
```Now Arora picks it up and I can install beta version of Adobe Flash easily by dropping it into ~/.mozilla/plugins.

---

### Post by lovinglinux on 2010-02-26
You can remove any conflicting plugins and install the appropriate version of flash with an [automated installer created by carlee](http://ubuntuforums.org/showthread.php?t=1414595).

For additional tips and instructions see the [COLOR="Sienna"]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Mustache Villain on 2010-03-01
Thanks for the links lovinglinux, they look really useful.

---

