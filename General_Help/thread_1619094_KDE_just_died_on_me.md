---
title: "KDE just died on me"
date: 2010-11-11
forum: General Help
---

### Post by lykwydchykyn on 2010-11-11
I was messing around with moving some plasmoids around in KDE, when something I did crashed plasma.  It wouldn't relaunch, so I just killed my session and restarted.

Now when I try to log in to KDE, it starts to login then kicks me out again. My .xsession-errors file contains this afterwards:
```

Xsession: X session started for alanm at Thu Nov 11 11:09:22 CST 2010
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
[: 225: ==: unexpected operator
xset:  bad font path element (#17), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax
startkde: Starting up...
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kded(4017): Communication problem with  "kded" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.ServiceUnknown" : " "The name org.kde.kded was not provided by any .service files" " 

startkde: Shutting down...
klauncher: Exiting on signal 1
startkde: Running shutdown scripts...
startkde: Done.


```


Here's what I know so far after trying to fix this:

 - renaming (defaulting) ~/.kde doesn't fix it
 - renaming ~/.local doesn't fix it
 - Other users can log in to KDE fine on this computer
 - I can log in to openbox on this computer

I'm stumped; usually if it's a user-specific problem it's something in ~/.kde.  Anyone help?

---

### Post by lykwydchykyn on 2010-11-11
Ok, I fixed it; I had to delete /var/tmp/kdecache-username.

Somehow it'd gotten corrupted; phoo, I killed my plasma-widgets layout in the process, though.  Careless mv command. :(

---

