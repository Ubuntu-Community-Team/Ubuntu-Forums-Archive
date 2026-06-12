---
title: "ubuntu-9.10-desktop-i386 Fresh Install Error"
date: 2010-03-22
forum: General Help
---

### Post by MasterPJ1987 on 2010-03-22
Defaulted everything.
 
This is my first time using linux. Im so fed up of things going wrong with windows: malware, spyware, viruses...damn the list is endless. So yeh Linux...
 
And get hit with two errors:
The panel encountered a problem while loading "OADIID:GNOME_IndicatorApplet"
The panel encountered a problem while loading "OADIID:GNOME_FastUserSwitchApplet"
 
Idiots guide please - step-by-step in how to get around these.
 
I have the option to "Dont Delete" or "Delete"
 
Im unsure why things would go wrong on such a fresh default install but Im willing to learn :D
 
Thanks,
Peter

---

### Post by 666f6f on 2010-03-22
You shouldn't get that error in a clean installation, unless you deselected some of the packages during installation.

Maybe I'm wrong but anyway, in order to fix the problem let's try to open a terminal/console and type:

```
sudo apt-get install gnome-applets
```

It's not my idea, I just *googled* my way arround ;)

---

### Post by MasterPJ1987 on 2010-03-22
Going to try a fresh install again.

---

### Post by 666f6f on 2010-03-22
Things hang, error messages appear.. pretty weird behaviour for a clean/default installation :-k

If things go bad again (highly doubt so), post here the output of ```
tail -n 2000 /var/log/messages
```

Also, try to create another user and logon using that new user and see if it works any better.

---

