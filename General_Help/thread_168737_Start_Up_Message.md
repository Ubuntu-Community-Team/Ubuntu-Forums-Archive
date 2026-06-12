---
title: "Start Up Message"
date: 2006-05-01
forum: General Help
---

### Post by CharlieC on 2006-05-01
Hi;

    Every time I boot up, once I get passed the initial sign in and get to the desktop I get a message to give my password to start firestarter. It reads something like I don't have permission to do /sbin/usr/firestarter or something like that. I don't even have firestarter installed. I made sure of that. I deleted everything I could think of but can't seem to cure the problem. 
    Does anyone have any suggestions on how I might fix this. It is not that big of a deal but it is annoying.

TIA
Charlie

---

### Post by iball on 2006-05-01
Obviously you don't want firestarter.

Try:
```
sudo apt-get remove firestarter
```
to remove it.  It seems that you are starting Firestarter whenever you log in to Gnome.  Go to System - Preferences - Sessions, and see if Firestarter is being started under "Startup programs"

I hope this helps
--Ian

---

### Post by CharlieC on 2006-05-01
So simple when you know how.
Thank you

Charlie

---

