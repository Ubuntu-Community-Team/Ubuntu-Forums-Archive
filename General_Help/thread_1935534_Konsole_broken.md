---
title: "Konsole broken"
date: 2012-03-04
forum: General Help
---

### Post by skeedo on 2012-03-04
I've recently moved from FreeBSD to Ubuntu. My home directory was copied over to my Ubuntu install, and it seems that configuration files created by Fbsd for certain applications have been causing some problems.

In Konsole, I do not get a right click menu. I tried renaming ~/[.kde|.kd4]/share/apps/konsole and ~/[.kde|.kd4]/share/config/konsole* as stated on KDE forums, however ran Konsole again and same problems. The follow errors are being outputted:

```

pit87:~/.kde/share/config> konsole &
[1] 24527
pit87:~/.kde/share/config> konsole(24528)/kdeui (kdelibs): Attempt to use QAction "change-profile" with KXMLGUIFactory! 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /usr/home/staff/skeedo/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 

[1]    Done                          konsole
pit87:~/.kde/share/config>

```Seems the problem is related to IBus...whatever that is. Any suggestions as to how to get it working normally? Thanks

---

### Post by skeedo on 2012-03-25
Alright, I did not realize I had to start up the IBUS daemon. I started it and I am no longer getting the IBUS errors, however still no right click menu :(

The following is outputted:

```

konsole(15847)/kdeui (kdelibs): Attempt to use QAction "change-profile" with KXMLGUIFactory!

```Anybody have suggestions? I need the ability to send text to all term tabs and afaik Konsole is the only software that will do this.

---

