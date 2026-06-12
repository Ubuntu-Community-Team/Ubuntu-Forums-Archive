---
title: "K3b crashing on startup"
date: 2010-11-24
forum: General Help
---

### Post by Muskiet on 2010-11-24
I've been using K3b for a long time on my Ubuntu 10.04 installation but today it decided to crash right after showing the splash screen.
When starting it in the terminal I get the following message:

>                       
 Error: "/var/tmp/kdecache-muskiet" is owned by uid 1000 instead of uid 0. 
 Error: "/tmp/kde-muskiet" is owned by uid 1000 instead of uid 0. 
 muskiet@muskiet:~$ Error: "/tmp/kde-muskiet" is owned by uid 1000 instead of uid 0. 
 Error: "/tmp/ksocket-muskiet" is owned by uid 1000 instead of uid 0. 
 kdeinit4: Shutting down running client. 
 kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so 
 Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString) 
 Error: "/tmp/ksocket-muskiet" is owned by uid 1000 instead of uid 0. 
 Error: "/tmp/kde-muskiet" is owned by uid 1000 instead of uid 0. 
 kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so 
 Error: "/var/tmp/kdecache-muskiet" is owned by uid 1000 instead of uid 0. 
 Error: "/tmp/kde-muskiet" is owned by uid 1000 instead of uid 0. 
 kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so 
 kbuildsycoca4 running... 
 Error: "/var/tmp/kdecache-muskiet" is owned by uid 1000 instead of uid 0. 
 kbuildsycoca4(2626) KBuildSycoca::checkTimestamps: checking file timestamps 
 kbuildsycoca4(2626) KBuildSycoca::checkTimestamps: timestamps check ok 
 kbuildsycoca4(2626) kdemain: Emitting notifyDatabaseChanged () 
 Error: "/var/tmp/kdecache-muskiet" is owned by uid 1000 instead of uid 0. 
 kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so 
 Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString) 
 k3b(2594)/kdeui (kdelibs): Attempt to use QAction "view_projects" with KXMLGUIFactory!  
 k3b(2594)/kdeui (kdelibs): Attempt to use QAction "view_dir_tree" with KXMLGUIFactory!  
 k3b(2594)/kdeui (kdelibs): Attempt to use QAction "view_contents" with KXMLGUIFactory!  
 k3b(2594)/kdeui (kdelibs): Attempt to use QAction "location_bar" with KXMLGUIFactory!  
 Error: "/tmp/ksocket-muskiet" is owned by uid 1000 instead of uid 0. 
 kdeinit4: preparing to launch /usr/lib/kde4/kio_trash.so 
 kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so 
 kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so 
 kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so 
 kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so 
 kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so 
 kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so 
 kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so 
 kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so 
 kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so 
 kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so 
 KCrash: Application 'k3b' crashing... 
 sock_file=/home/muskiet/.kde/socket-muskiet/kdeinit4__0 
 kdeinit4: preparing to launch /usr/lib/kde4/libexec/drkonqi 
 Error: "/var/tmp/kdecache-muskiet" is owned by uid 1000 instead of uid 0. 
 Error: "/tmp/kde-muskiet" is owned by uid 1000 instead of uid 0. 
 Looks to me like some sort of ownership issue?
Could anybody please help me with this?

---

### Post by viralmeme on 2010-11-24
> **Muskiet said:**
> Looks to me like some sort of ownership issue? Could anybody please help me with this?
Delete the referred to directories ..

$rm -r /var/tmp/kdecache-muskiet /tmp/kde-muskiet ..

---

