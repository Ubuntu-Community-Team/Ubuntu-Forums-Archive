---
title: "HPLIP not working in jaunty (part deux)"
date: 2009-07-17
forum: General Help
---

### Post by WildSioux on 2009-07-17
Just as this thread states...I have HPLIP installed with a working HP 6280.  I am able to print.  But I am unable to open the HP-toolbox or the HP Devicemanager from the tray icon.

[http://ubuntuforums.org/showthread.php?t=1108108&highlight=hplip+toolbox+doesn%27t+open]("http://ubuntuforums.org/showthread.php?t=1108108&highlight=hplip+toolbox+doesn%27t+open")

This is what I get in CLI
```
hp-toolbox

HP Linux Imaging and Printing System (ver. 3.9.2)
HP Device Manager ver. 15.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Traceback (most recent call last):
  File "/usr/bin/hp-toolbox", line 246, in <module>
    from ui4.devmgr5 import DevMgr5
  File "/usr/share/hplip/ui4/devmgr5.py", line 45, in <module>
    from dbus.mainloop.qt import DBusQtMainLoop
ImportError: No module named qt

```

Since I am running KDE 4.3 RC2, I believe it is something to do with KDE and QT.  But not sure how to fix.

Thanks

---

### Post by ibutho on 2009-07-17
Try install pyqt or pyqt4.

---

### Post by coffeecat on 2009-07-17
First thing - the thread you linked was about a python bug that broke a lot of applications (including hplip) when Jaunty was still in Beta. It was fixed within hours so it's not relevant now.

Have you got the package hplip-gui installed? That brings in load of python and qt4 dependencies, so that might be the answer. Although having said that, I notice you talk about the tray icon which I thought was part of hplip-gui. Whatever - hplip-gui doesn't come as part of a default install so if you haven't installed it, it might be worth doing so.

---

### Post by WildSioux on 2009-07-17
Yes, I already have python-qt4-dbus and the hplip-gui installed.  

I believe this is the problem.  But I don't know where to go from here since I have everything installed.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=520789]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=520789")

IN LINE EDIT...found the solution:
I downloaded the python-qt4-dbus deb (4.5.2-0ubuntu1) from the Karmic repo.  Installed it, and now it opens happily showing my previously installed printer, ink levels, etc...

[http://packages.ubuntu.com/karmic/python-qt4-dbus]("http://packages.ubuntu.com/karmic/python-qt4-dbus")

The jaunty python-qt4-dbus 4.4.4-2ubuntu6 isn't working for some reason???

EDIT:  Not sure how to mark this thread as solved.  Or mods may choose to leave open for others if they have this problem.  Thanks

---

### Post by coffeecat on 2009-07-17
I'm glad you've got it sorted, but...

> **WildSioux said:**
> The jaunty python-qt4-dbus 4.4.4-2ubuntu6 isn't working for some reason???

Well - it must be working for me because that's the version I have installed in my Jaunty and my hplip/hplip-gui is working just fine.

Perhaps your python-qt4-dbus had got broken or corrupted somehow and a simple reinstall of it would have fixed the problem, but as you've fixed it with a later version it probably doesn't matter now.

---

### Post by WildSioux on 2009-07-18
> **coffeecat said:**
> I'm glad you've got it sorted, but...



Well - it must be working for me because that's the version I have installed in my Jaunty and my hplip/hplip-gui is working just fine.

Perhaps your python-qt4-dbus had got broken or corrupted somehow and a simple reinstall of it would have fixed the problem, but as you've fixed it with a later version it probably doesn't matter now.

Well if it works for you thats good.  I believe my problem may be isolated since I am running KDE 4.3 RC2 from kubuntu backports.  So something may be broken with using the python-qt4-dbus from jaunty with the KDE 4.3 RC2.

I even tried purging everything related to hplip,python,etc... and reinstalling the jaunty version of python-qt4-dbus.  It still didn't work which is why I came on in after that failed.  And after installing the one from karmic, I purged everthing again and went back to the jaunty one thinking it may have fixed something...but no luck.

It makes sense that the one from the karmic repo works since KDE 4.3 will be in karmic.

---

### Post by coffeecat on 2009-07-19
> **WildSioux said:**
> I believe my problem may be isolated since I am running KDE 4.3 RC2 from kubuntu backports.

...


It makes sense that the one from the karmic repo works since KDE 4.3 will be in karmic.

Yes, agreed. Good point.

---

### Post by cggaret on 2009-07-26
I fixed this in my Ubuntu installation by going to HP and installing the newest hplip ver. 3.9.6b.

---

### Post by SuporteTecnicoID on 2009-10-17
> **cggaret said:**
> I fixed this in my Ubuntu installation by going to HP and installing the newest hplip ver. 3.9.6b.



[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

sudo apt-get install --reinstall --assume-yes python-qt4-dbus

hp-toolbox     -> ok!

:):):)

---

