---
title: "Disable Password on Logout?/Shutdown?"
date: 2012-01-15
forum: General Help
---

### Post by davethewave83 on 2012-01-15
When logging out today during a power-outage, a box popped up saying I needed to give it my password (to shut down) :confused: I gave it my password, but I guess I typed it wrong as it popped up again, I gave it my password, it popped up again (I was trying to hurry as the power was failing due to a heavy snow) it wouldn't take my password, so I just hit the power button for 8 seconds and killed the machine improper. 

Is there a way to disable this from happening? It never usually does this, I don't know why it did this time. 

I guess I can just enable root and login as that all the time, but I'd rather an alternative if possible.

---

### Post by corrytonapple on 2012-01-15
One of the many golden rules of Linux, and I am unsure if you meant the GUI of root, never login as root account from the login screen.  It can destroy your system.
Are you admin on your system?  Are you using SLIM?  Are you on 11.10 or 10.04?

And yeah, the weather is suddenly getting cRaZy

---

### Post by davethewave83 on 2012-01-15
> **corrytonapple said:**
> One of the many golden rules of Linux, and I am unsure if you meant the GUI of root, never login as root account from the login screen.  It can destroy your system.
Are you admin on your system?  Are you using SLIM?  Are you on 11.10 or 10.04?

And yeah, the weather is suddenly getting cRaZy

Yeah i'm Admin, what's slim? there's a slim chance I'm using it as i don't know what it is ;)

---

### Post by corrytonapple on 2012-01-15
You're not using it then :P
SLIM is an alternative to LightDM, or GDM, or KDM, your login screen.
Debian had a KILLER BUG that made it so when you logged in from SLIM, it wouldn't load consolekit, and you couldn't do anything, such as suspend or change WiFi networks.

Hmm, you are admin.... what happens if you do it from the command line?
```
sudo shutdown -h now
```
Enter your password, it won't show up.

---

### Post by wildmanne39 on 2012-01-15
Hi, I suspect it was caused by a glitch it should not have asked for your password to turn off and here is a link for shutting down your computer safely when it is frozen or not responding.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Thanks

---

