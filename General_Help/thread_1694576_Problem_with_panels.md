---
title: "Problem with panels"
date: 2011-02-24
forum: General Help
---

### Post by _silverSpoon on 2011-02-24
I am using Ubuntu 10.04 Lucid Lynx, and accidently i today added an extra panel and changed its orientation to TOP and set AUTOHIDE to True.
The Top panel stopped showing, quite obvious and i got scared. So, I though that if i just do a forceful shut down, it will not save any preferences. So, Using the Switch ON/OFF button, i turned off the PC.
Now, when I try to turn my Ubuntu back on, it is not loading up properly. None of the panels show up, and the system hangs.

Is there a way, that I can get my system back on working?? I have lot of work lined up, and I don't want to re-install as I have downloaded and installed a lot of packages, and configured them.

I have tried loading in GNOME fail-safe mode but the same thing happens. I tried loading in xterm mode, but i didn't know what to do next.

Please help me.

---

### Post by Habitual on 2011-02-24
Logout of the GUI. then
Ctrl+Alt+F1
Login.
```
mv ~/.config ~/.config.org
mv ~/.gconf ~/.gconf.org
exit
```
Ctrl+Alt+F7 and login

Panels!

---

