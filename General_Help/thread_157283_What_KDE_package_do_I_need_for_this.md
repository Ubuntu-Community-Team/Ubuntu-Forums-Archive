---
title: "What KDE package do I need for this?"
date: 2006-04-08
forum: General Help
---

### Post by Greeface on 2006-04-08
When I try to run "WebControl" in amaroK it "exits with error code 1:"
```
sh: kdialog: command not found
Traceback (most recent call last):
File "/usr/share/apps/amarok/scripts/webcontrol/WebControl.py", line 42, in ?
from qt import *
ImportError: No module named qt
```

What package(s) do I need to get "kdialog" and "qt"?  I googled them but I wasn't able to find anything.

Thanks

---

### Post by ksudbury on 2006-04-08
IIRC qt = apt-get install libqt3-mt

---

### Post by Greeface on 2006-04-08
Okay, I installed it but it still gives the the same message.  Do I have to 'modprobe' it or something?  I don't know much about it.

Thanks for the help

---

### Post by starsky51 on 2006-09-10
I realise the question was asked a few months ago but since i had trouble finding a solution myself, i thought i'd post my own.
The package which contains kdialog is called kdebase-bin.
So:
sudo apt-get install kdebase-bin

---

