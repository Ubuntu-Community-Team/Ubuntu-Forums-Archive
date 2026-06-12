---
title: "Help! Taskbar is gone"
date: 2011-08-28
forum: General Help
---

### Post by Duty on 2011-08-28
the following happened to me:
after having installed one update, enabled a new driver for nvidia and having installed timidity i shut down my laptop (samsung r510)
the next time it turned it on, everything was quite normal untill before tipping in your password there was something written about timidity, then normal password entering and the &#324; it happened:
MY TASKBAR DID'NT START UP!
is there anybody able to tell me, what i can do?

---

### Post by miasmablk on 2011-08-28
did you try restarting Unity?

alt + f2 unity

---

### Post by Duty on 2011-08-28
biggest problem is the terminal isn't starting, when i hit alt+f2

---

### Post by miasmablk on 2011-08-28
try creating a desktop launcher then for unity. by right clicking on the desktop selectin create launcher. the launcher type should be "application"


name: Unity

description:

command: /usr/bin/unity

comment:

---

### Post by Duty on 2011-08-28
doesn't work either
the starter is there, but when i click on it all symbols on my desktop flare for half a second and nothing happens...

---

### Post by miasmablk on 2011-08-28
or just log out then log back in by pressing:

alt + Prnt Scrn + k

simultaneously

---

### Post by Duty on 2011-08-28
nothing...

---

### Post by miasmablk on 2011-08-28
maybe check your settings in ccsm? check to see that OpenGL, compostite, gnome compatability, and unity plugin are all enabled.

---

### Post by Duty on 2011-08-28
how to get there?
(where i can check this stuff)

---

### Post by miasmablk on 2011-08-28
ctrl + alt + t

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by miasmablk on 2011-08-28
after the install is finished just open compiz config settings manager either in the dashboard or just type ccsm in the terminal.

ctrl + alt + t
```
ccsm
```

---

### Post by Duty on 2011-08-28
i already have compizconfig installed, but can't start it without the taskbar
even alt+t doesn't work, can't open my terminal!
crap!

---

### Post by Duty on 2011-08-28
the taskbar appeared!
i rebootet with generic and then choose secure graphic mode and there is the toolbar and the taskbar again...
i'll deinstall the latest installations and then it should work :)
eventhough thx for your help

---

### Post by miasmablk on 2011-08-28
> **Duty said:**
> the taskbar appeared!
i rebootet with generic and then choose secure graphic mode and there is the toolbar and the taskbar again...
i'll deinstall the latest installations and then it should work :)
eventhough thx for your help

cool, good job :D

---

