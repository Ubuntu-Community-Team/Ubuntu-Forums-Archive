---
title: "Will this harm anything"
date: 2009-11-07
forum: General Help
---

### Post by RJ12 on 2009-11-07
I want to install Xchat but when I do it says this



The following packages were automatically installed and are no longer required:
  python-alsaaudio python-awn-extras python-sqlalchemy python-awn libawn0
  python-utidylib libtidy-0.99-0 libawn-extras0 python-feedparser
  avant-window-navigator-data python-dateutil python-awnlib sqlite3
  python-xlib python-chardet


Will this harm anything please I dont want to not be able to log in...

please I see stuff that might not want to be removed

---

### Post by jimmy the saint on 2009-11-07
They are likely dependencies for software you have since removed.  That software required them, but since you removed it, you no longer need them.

---

### Post by RJ12 on 2009-11-07
but what about alsaaudio? it says 1 package newely installed 0 upgraded 193 (or more I think) not changed so maybe it is safe what do you guys think

---

### Post by nothingspecial on 2009-11-07
Those have nothing to do with xchat.

They are dependencies, still installed on your system, that you don`t need, due to removing packages that depend on them.

You can leave them there or type

```
sudo apt-get autoremove 
```

to get rid of them.

---

### Post by RJ12 on 2009-11-07
Ok so if I install Xchat nothing will happen to my system and nothing will break?
Becuase alsa audio looks important?

---

### Post by Labello on 2009-11-07
right! =)

---

### Post by nothingspecial on 2009-11-07
> **RJ12 said:**
> Ok so if I install Xchat nothing will happen to my system and nothing will break?
Becuase alsa audio looks important?

Well I`m not going to garuntee it, because I`m not a Ubuntu/xchat/etc dev ..... but I`d do it without worry.

---

### Post by RJ12 on 2009-11-07
Well so far everything works thanks guys!!



*Marks as Solved*

---

