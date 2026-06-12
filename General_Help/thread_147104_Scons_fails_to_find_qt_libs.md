---
title: "Scons fails to find qt libs"
date: 2006-03-19
forum: General Help
---

### Post by exhuma.twn on 2006-03-19
Hi,

I recently wanted to compile [madman]("http://madman.sf.net"). But when running *scons* I get this:

```
exhuma@inevitable:~/madman--production--1.0--patch-37$ ./scons.py
scons: Reading SConscript files ...
Checking for qt at /usr/share/qt3/lib (with lib) failed
Checking for qt-mt at /usr/share/qt3/lib (with lib) failed
Checking for qt at /usr/share/qt3 (with lib) failed
Checking for qt-mt at /usr/share/qt3 (with lib) failed
Checking for qt at /usr/share/qt (with lib) failed
Checking for qt-mt at /usr/share/qt (with lib) failed
Checking for qt at /usr (with lib) failed
Checking for qt-mt at /usr (with lib) failed
Checking for qt at /usr/local (with lib) failed
Checking for qt-mt at /usr/local (with lib) failed
Checking for qt at /usr/lib/qt3 (with lib) failed
Checking for qt-mt at /usr/lib/qt3 (with lib) failed
Checking for qt at /usr/lib/qt (with lib) failed
Checking for qt-mt at /usr/lib/qt (with lib) failed
Checking for qt at /usr/share/qt3/lib (with lib64) failed
Checking for qt-mt at /usr/share/qt3/lib (with lib64) failed
Checking for qt at /usr/share/qt3 (with lib64) failed
Checking for qt-mt at /usr/share/qt3 (with lib64) failed
Checking for qt at /usr/share/qt (with lib64) failed
Checking for qt-mt at /usr/share/qt (with lib64) failed
Checking for qt at /usr (with lib64) failed
Checking for qt-mt at /usr (with lib64) failed
Checking for qt at /usr/local (with lib64) failed
Checking for qt-mt at /usr/local (with lib64) failed
Checking for qt at /usr/lib/qt3 (with lib64) failed
Checking for qt-mt at /usr/lib/qt3 (with lib64) failed
Checking for qt at /usr/lib/qt (with lib64) failed
Checking for qt-mt at /usr/lib/qt (with lib64) failed
```

I suppose I am missing a package containing the qt headers, but I don't know which one to look for.  I do have installed libqt3-headers. Yet no luck.

Some more info:
```
exhuma@inevitable:~/madman--production--1.0--patch-37$ dpkg -l | grep qt
ii  gtk2-engines-gtk-qt                             0.60-1ubuntu5
ii  libdbus-qt-1-1c2                                0.36.2-0ubuntu7
ii  libqt-perl                                      3.008-1.3build1
ii  libqt3-compat-headers                           3.3.4-8ubuntu5
ii  libqt3-headers                                  3.3.4-8ubuntu5
ii  libqt3-mt                                       3.3.4-8ubuntu5
ii  libqt3-mt-dev                                   3.3.4-8ubuntu5
ii  libsmokeqt1                                     3.4.3-0ubuntu2
ii  python-qt3                                      3.14.1-2ubuntu4
ii  python2.4-qt3                                   3.14.1-2ubuntu4
ii  python2.4-sip4-qt3                              4.2.1-1ubuntu4
ii  qt3-dev-tools                                   3.3.4-8ubuntu5
```

Any idea is greatly appreciated ;)

---

### Post by exhuma.twn on 2006-04-03
bump

---

### Post by ktulu1115 on 2006-06-08
I have the same problem.  For the life of me, I couldn't figure out what the problem was.  Tried passing several different paths to the qt_directory option...  but no luck.  Anyone else?

---

### Post by ktulu1115 on 2006-06-12
bump...  anyone?

---

### Post by ktulu1115 on 2006-06-17
This is going to sound really dumb...  but try doing an 'apt-get install g++'.  That was my problem. :mad:

---

### Post by analysisrex on 2006-06-17
I had the same problem with scons while trying to manually complie rosegarden (the synaptic install didn't load the sequencer, and it wasn't fully functional).  I also already had installed the qt libs, however I saw on another forum that they installed the general kde libs and it fixed the problem.

I just installed what looked to be core kde libs in synaptic, installed them, and this error went away.


hope that helps,
analysis

---

