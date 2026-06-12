---
title: "Keyboard and Mouse dont work after update crash.."
date: 2009-07-15
forum: General Help
---

### Post by Kaneda187 on 2009-07-15
My Keyboard and Mouse dont work after i recently updated I ran recovery mode still nothing, works I can only get to my login screen then nothing works i cant type anything i cant move the mouse!
After i ran recovery mode then shut down i get this message....```
Encountered error' error in file /etc/dbus-1/system.d/hal.conf' line 1, colume 0 
:no element found
' while parsing /etc/dbus-1/system.d/hal.conf' 
```

Im using ubumtu 9.04 this happened when my laptop crashed while updating any ideas?

---

### Post by Kraut~salat on 2009-07-15
by login screen you mean the X login screen, I suspect. Your regular console does still work? 
So obviously your HAL is broken/configfile empty. I would just try to reinstall HAL via console.

---

### Post by Kaneda187 on 2009-07-15
How would i go about doing that?

---

### Post by Kaneda187 on 2009-07-15
What is the command to reinstall hal? and what do I need? disk or wired internet connection?

---

### Post by Kraut~salat on 2009-07-16
you would need an internet connection and familiarise yourself withthe apt-get command. reading the man pages (man apt-get) will tell you how to help. But it is not my task to tell you what command to type in.  Reading documentation is mandatory if you want to use Linux, especially on a key thing like installing things.

[http://www.debian.org/doc/manuals/apt-howto/index.en.html#contents](http://www.debian.org/doc/manuals/apt-howto/index.en.html#contents)

here you can find a primer on that. It will tell you how to force the reinstall of a packet

---

### Post by Kaneda187 on 2009-07-16
Thanks! Ill have a read of this later and ill let you know how i get on. cheers

---

