---
title: "gnome-do not showing any plugins"
date: 2010-03-06
forum: General Help
---

### Post by woodsonoversoul on 2010-03-06
It's only showing Battery Docklet, CPU Monitor Docklet, Switcher Docklet, and Weather Docklet, and no plugins. It's a fresh install, why can't I see any/more?

---

### Post by mk1w86 on 2010-03-06
You might be looking in the wrong place, is it under the Plugins tab in Preferences you are looking at?

Also are you actually using Ubuntu 7.04 like your profile says?

---

### Post by woodsonoversoul on 2010-03-07
No, just upgraded to 9.10 this weekend. Looking under preferences>plugins>all plugins. Only see those 4 docklets...

---

### Post by mk1w86 on 2010-03-07
Try running:

```
sudo aptitude install gnome-do-plugins
```

which should install the plugins, although when I installed Gnome Do by running

```
sudo aptitude install gnome-do
```

both the plugins and the docklets packages were installed automatically. :-k

---

### Post by woodsonoversoul on 2010-03-07
Fixed it. Thanks man

---

