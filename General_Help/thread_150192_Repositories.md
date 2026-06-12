---
title: "Repositories"
date: 2006-03-25
forum: General Help
---

### Post by dc2447 on 2006-03-25
Wierd one, I have rebuilt this wokstation a few times, I was trying to install acidrip tonight but it isn't found in the repositories - I can't see what I am missing - anyone point me in the right direction?



> davidcam@han:/data/music$ cat /etc/apt/sources.list
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.1/kubuntu](http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.1/kubuntu) breezy main
davidcam@han:/data/music$                                                                        

---

### Post by Barrakketh on 2006-03-25
You're missing multiverse:
```
deb http://gb.archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu breezy multiverse
```

Next time, try searching for the package at [http://packages.ubuntu.com](http://packages.ubuntu.com).  It will tell you which repository a package is located in.

---

### Post by dc2447 on 2006-03-25
[QUOTE=Barrakketh]You're missing multiverse:
```
deb http://gb.archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu breezy multiverse
```

Next time, try searching for the package at [http://packages.ubuntu.com](http://packages.ubuntu.com).  It will tell you which repository a package is located in.[/QUOTE]

Thanks, that is really helpful

---

