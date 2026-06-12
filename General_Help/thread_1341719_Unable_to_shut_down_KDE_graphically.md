---
title: "Unable to shut down KDE graphically"
date: 2009-11-30
forum: General Help
---

### Post by Gavagai80 on 2009-11-30
Though I can do an sudo shutdown -P now from konsole, that doesn't save the KDE session so I really want to shut down the right way. Clicking the normal shutdown menu item will grey the screen, but once the timer runs down or I click to shutdown now everything goes back to normal like it forgets the request. So I decided to run the kshutdown program. Running as regular user, it behaves the same as the menu item -- just silently doesn't shut down. Running it with sudo I get this:
```
pgk@pgk-laptop:~$ findServiceByDesktopPath: kgrubeditor.desktop not found
sudo kshutdown                                                           
[sudo] password for pgk:                                                 
GDM = 0                                                                  
GNOME = 0                                                                
KDE Full Session = 0                                                     
KDE 3 = 0                                                                
KDE 4 = 0                                                                
KDM = 0                                                                  
Error: "/var/tmp/kdecache-pgk" is owned by uid 1000 instead of uid 0.    
Error: "/tmp/kde-pgk" is owned by uid 1000 instead of uid 0.
pgk@pgk-laptop:~$ Error: "/tmp/kde-pgk" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-pgk" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
Error: "/tmp/ksocket-pgk" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-pgk" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
Error: "/var/tmp/kdecache-pgk" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-pgk" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-pgk" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-pgk" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-pgk" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
kdeinit4: preparing to launch /usr/bin/knotify4
Error: "/var/tmp/kdecache-pgk" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-pgk" is owned by uid 1000 instead of uid 0.
```
And visually, there's a popup saying "Could not logout properly. Session manager cannot be contacted."

Can anyone give me a hint as to whether the above output is relevant or means anything? Or at least tell me if kshutdown should be run with or without the sudo?

Please note: suspending and hibernating (suspend to disk) works fine, it's just shutting down and rebooting that don't.

As regular user, running kshutdown -h:
```
pgk@pgk-laptop:~$ kshutdown -h
GDM = 0
GNOME = 0
KDE Full Session = 1
KDE 3 = 0
KDE 4 = 1
KDM = 1
pgk@pgk-laptop:~$

```

---

### Post by ooolongT on 2009-11-30
I am having similar issues, and I am not sure why.  Mine are not as serious, I can shut down but I am getting the 
```

Error: "/var/tmp/kdecache-XXXXX" is owned by uid 1000 instead of uid 0.
```

I am sure I can change the permissions on that file, but I sure would like to know why I am getting this error when I open and close programs.

---

### Post by KIAaze on 2010-03-04
I'm having the same problem from time to time.
Here's the bug report I made a while back: [https://bugs.kde.org/show_bug.cgi?id=213541](https://bugs.kde.org/show_bug.cgi?id=213541)

Can't shut down at the moment. :/

---

