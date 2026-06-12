---
title: "Stuck at command prompt login"
date: 2010-01-29
forum: General Help
---

### Post by jacksterson on 2010-01-29
Hey, I've used Ubuntu for about 3 months last year, and decided to come back to it.  Have had it installed for about a week, no problems (Besides the stupid proprietary drivers and broadcom issues, but I've figured those out).

So today I tried playing san andreas, which required that I do some things with xorg and/or dirc or something.  I followed some guides, and about 2 hours of messing around, finally got the graphics to display correctly in the game, but when I restarted I'm stuck at a command prompt login screen that says 'tty1' at the top.

I've tried resetting xorg to defaults, and startx, and /etc/init.d/gdm start but none of that works.  Any ideas?

*EDIT*
After messing around, I found out that I don't have /etc/x11 or whatever.  its not there.  Tried recovery mode, tried updating, upgrading, etc, nothing worked.  Next up is sudo apt-get install ubuntu-desktop.

I really don't want to reinstall, it took me 3 straight days of configuring to get it the way i wanted it...

---

### Post by jacksterson on 2010-01-29
bump

---

### Post by wojox on 2010-01-29
It should be a capital X

```
cd /etc/X11/
```

see if you have a xorg.conf.failsafe file.

---

### Post by jacksterson on 2010-01-29
I don't see any failsafe file, just xorg.conf and xorg.conf.20100129151621

---

### Post by wojox on 2010-01-29
Okay try this:

```
sudo cp xorg.conf.20100129151621 xorg.conf
```

You'll need to be in /etc/X11 Directory for that. And reboot.

---

### Post by jacksterson on 2010-01-29
Alright, and if it helps any, heres the website(s) that I did stuff with that is most likely relevant to my problem:

[http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html](http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html)
[http://dri.freedesktop.org/wiki/Download](http://dri.freedesktop.org/wiki/Download)  (in here I did a makefile with one of the externals libs)

---

### Post by jacksterson on 2010-01-29
No dice.  nothing worked, also though, i noticed it said that /etc/X11/X does not exist, though i saw it earlier while i was in that specific folder...  i even cd'd to it and tried running 'startx' but still gave the same error...

---

### Post by wojox on 2010-01-29
Did you do all this here:

```

# cat >> /etc/apt/sources.list
deb http://ftp.debian.org/debian/ unstable main
^D
# apt-get update
# apt-get -t unstable install xserver-xorg

```

---

### Post by jacksterson on 2010-01-29
Tried to, first one didn't work, second one didn't do anything, third one got an error.  Most of the stuff I tried got errors, until I finally got Dirc from ubuntu software center.

---

### Post by wojox on 2010-01-29
No x huh? Try reinstalling:

```
sudo apt-get install --reinstall xserver-xorg
```

---

### Post by jacksterson on 2010-01-29
from live cd, or within command prompt?

---

### Post by jacksterson on 2010-01-29
Well, after doing it, nothing happened, so I typed 'startx' and it worked.  I'm now on it, so I stayed on for a while before I posted so I could restart and see if it still worked.  Well, clicking restart only brought me back to the command prompt...

---

