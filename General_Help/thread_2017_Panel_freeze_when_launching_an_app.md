---
title: "Panel freeze when launching an app"
date: 2004-10-25
forum: General Help
---

### Post by multani on 2004-10-25
Hi,

I am using Ubuntu for a week now, but I've got a strange problem : when I launch an application throught a panel (or a terminal from the desktop-menu), the panel seems to freeze for about 30sec.
While the panel is freezing, the application isn't launching, but only about 30sec. later :/

The problem doesn't appear when I start an app from a terminal. And, of course, I got nothing interesting in log, nor in ~.xsession-errors :(

Is anyone got this problem ? Is there a soluce, or where can I find more informations about it ?

---

### Post by umarmung on 2004-10-25
This might be a wild guess, but do you use any packetfilter like iptables?

---

### Post by multani on 2004-10-25
Hum, not yet :/

---

### Post by multani on 2004-10-27
I thought i have founded where the problem lies : i had remove all my ~.gnome*, ~.gconf* and ~.metacity* file and then, it started to work as normal (no problem, etc.)

But this morning, Gnome doesn't want to start. In fact, it does, but terribly slow (I can see the splash screen after 20sec., and then, nothing more).
I have done the same things as I did before (remove my Gnome configuration file from my home directory), but this time, it has no effect.

After doing some kill stuff on dbus and bonobo-activati*, I can get the things to start, unusually slow.
When I wanted to change my settings (remember, i have deleted all of them ;) ), I got an "Avertissement" window, but with nothing in.

And, i got this weird things in my log :
```
kernel: mtrr: 0xe0000000,0x1000000 overlaps existing 0xe0000000,0x400000
```

---

