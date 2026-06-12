---
title: "Missing global menu"
date: 2012-05-06
forum: General Help
---

### Post by jonny on 2012-05-06
I've just upgraded from Ubuntu 10.04 Lucid to Precise, but I don't have global menubars in any applications - the menus remain stubbornly attached to individual windows instead.  I've tried reinstalling the relevant packages ```
sudo apt-get install --reinstall appmenu-gtk3 appmenu-gtk appmenu-qt
``` and I've also attempted to install lo-menubar, but nothing happens.  the problem afflicts all users on the system, and on a presumably related note, HUD searches produce no results for me.

Any ideas?

---

### Post by jonny on 2012-05-06
Not sure why this thread is labelled as Lubuntu.  I'm actually using normal Ubuntu, and can't work out how to change it.

---

### Post by jonny on 2012-06-25
In answer to my own question - in case anyone finds this through Google - I simply needed to install indicator-appmenu, thus:
```
sudo apt-get install indicator-appmenu
```

---

### Post by ranger1021994 on 2012-06-25
U can use MyUnity/Unsettings/Ubuntu Tweak to enable global menu in Precise
:)
but i guess its enabled by default nd works fine with me..

---

