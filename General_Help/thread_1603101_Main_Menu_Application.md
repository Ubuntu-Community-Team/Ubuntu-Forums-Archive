---
title: "Main Menu Application"
date: 2010-10-22
forum: General Help
---

### Post by roadkillguy on 2010-10-22
I've created an application and I'd like to add it to the Launcher.  I've tried using Main Menu, but it still doesn't show up when I search for it.

I'm using UNR 10.10.  Just downloaded yesterday :D

---

### Post by jerrrys on 2010-10-23
there's too much of a difference between standard ubuntu and remix; so i cant tell you how to do it, but i can point you here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+launcher+unr&as_qdr=all&sa=Google+Search&lang=en#1117](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+launcher+unr&as_qdr=all&sa=Google+Search&lang=en#1117)

---

### Post by kerry_s on 2010-10-23
> **roadkillguy said:**
> I've created an application and I'd like to add it to the Launcher.  I've tried using Main Menu, but it still doesn't show up when I search for it.

I'm using UNR 10.10.  Just downloaded yesterday :D

when you add something, you need to log out & back in for it to show in the menu.

---

### Post by roadkillguy on 2010-10-23
...That didn't work.  Does Main Menu have any connection with the new UNR Unity interface?  Nothing is being added or removed, whereas in the old one it happened instantly.

I think I'm just going to stick with desktop mode now.  Unity kinda sucks, and is slow.  Do you guys know how to revert back?

---

### Post by Jebtrix on 2010-10-23
Unity fails to start under virtualbox but it looks like it pulls shortcuts from /usr/share/applications among others
To revert try:

```
sudo apt-get remove unity 
sudo apt-get autoremove
```

---

### Post by roadkillguy on 2010-10-23
Hmmm... I think the previous menu was uninstalled.  Removing Unity only gives a white screen, and a mouse.

Is there a command to install the old UNR Launcher?  I'm currently using desktop mode.

---

