---
title: "Xmind has no menu in natty 11.04 Unity"
date: 2011-05-17
forum: General Help
---

### Post by thetechnaddict on 2011-05-17
The application Xmind has no menu when running in Unity - (at least in 64 bit)

One day I hope this will play nicely with the global menu - 

Meanwhile here's a work-around - 

from the terminal type:

gksudo gedit /usr/share/applications/xmind.desktop

In the editor add "env Ubuntu_MENUPROXY=0" to the Exec section - the whole line should look like this:

Exec=env UBUNTU_MENUPROXY=0 /usr/local/xmind/xmind

Now Xmind will not use the Unity's global menu, but you will see a menu!

---

### Post by dennmans on 2011-05-28
please note: use capitals - so UBUNTU_MENUPROXY=0 and not Ubuntu... etc.

---

### Post by masat on 2011-06-29
Thanks! that worked for me, however I needed a reboot to see the changes

---

### Post by prokher on 2011-07-13
Great, that works well w/o reboot.

---

