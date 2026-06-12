---
title: "xmodmap script does not work as a startup application"
date: 2010-08-19
forum: General Help
---

### Post by sa-mejia on 2010-08-19
In previous versions of ubuntu I used to reshuffle the ALT, SHIFT, and TAB keys using xmodmap.  

Specifically, I had a file called ~/.xmodmap-mejia which reshuffled the keyboard, and I called that file from the startup applications (I had added it to system>preferences>Startup Applications). 

However, in Ubuntu 10.4 it does not work.  If I call the script after the computer has loaded, it works perfectly, but it does not have any effect as a startup application.   It is as though changes effected by the script that calls ~/.xmodmap-mejia gets overwritten later on by the default keyboard binding.

As things stand right now, I have to run the script manually every time I turn on my laptop.  Which, of course, is very annoying.

Any ideas of how to fix this?

---

### Post by sa-mejia on 2010-08-20
bump

---

### Post by hal8000 on 2010-08-20
Not sure why its stopped working, then you check your script is executable 
from the location in startup applications.

There are also other ways of running scripts:
adding to rc.local
creating a new service for runlevel 2

or possibly adding your script to
~/.xinitrc

or global xinitrc at

/etc/X11/xinit/xinitrc

I'm not sure which is the preferred Ubuntu Lucid choice though.

---

### Post by sa-mejia on 2011-01-29
bump

---

### Post by sa-mejia on 2011-01-30
By looking through the internet, I found two solutions to the problem:

1. (Not very elegant one) To put in the script

sleep 10 && xmodmap /home/canti/.xmodmap-mejia

(instead of the previous: "xmodmap /home/canti/.xmodmap-mejia").  This makes xmodmap activate 10 second later, and, thus, kicks in after the default bindings have.

2. To add a new file, under "\home\youruser" (i.e. under "~") that begins with .xmodmap (say .xmodmap-mejia2).  The next time one reboots the computer, a window appears asking you if you want to load any of your .xmodmap files under ~.  You have to ask the window to load which ever file you want every time it opens.

---

### Post by daniel.hartman on 2011-06-04
Yep, same problem here with Ubuntu 10.10.  I am trying to disable the Synaptics Touchpad for my eighty year-old mother-in-law.  

The following command works great in a console, but it does not work when you add it to the Startup Applications (under System => Preferences => Startup Applications):

```
xinput set-prop 12 "Device Enabled" 0
```

I like your sleep option.  Worked perfectly.  

It would be nice to know why it does not work without the sleep, must be something with X still initializing.  It is unclear how one might go about debugging the execution sequence here.

Thank you for your follow up.

---

