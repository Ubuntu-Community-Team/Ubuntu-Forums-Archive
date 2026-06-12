---
title: "HPLIP toolbox doesn't find QT4"
date: 2010-08-25
forum: General Help
---

### Post by Bob Morane on 2010-08-25
Hello, i have troubles using various HPLIP applications (HPLIP toolbox, HP setup, HP systray icon) because it doesn't find QT4. However i have qt4 installed (at least i think so, there are quite a few QT4 packages available, and i can't a metapackage that will install everything needed but qt4core, qt4gui and a bunch others are instlalled. pyqt4 is installed.

[**See the solution in this post**]("http://ubuntuforums.org/showpost.php?p=9899503&postcount=5")

Here is what i get if i try to run hp-setup
```
HP Linux Imaging and Printing System (ver. 3.10.2)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Unable to load Qt4 support. Is it installed?
```
And here is the result of hp-check -r
```
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

Distribution:
ubuntu 10.04

Checking Python version...
OK, version 2.6.5 installed

Checking PyQt 4.x version...
Traceback (most recent call last):
  File "/usr/bin/hp-check", line 304, in <module>
    from PyQt4 import QtCore
ImportError: /usr/lib/pymodules/python2.6/PyQt4/QtCore.so: undefined symbol: _ZN13QStateMachine22beginSelectTransitionsEP6QEvent
```
I already tried reinstalling both pyqt and hplip. Nothing works.

---

### Post by TNT1 on 2010-08-25
Check with Synaptic if QT4 is installed?

---

### Post by Bob Morane on 2010-08-26
Which one of those do i need to install exactly?
```
dpkg -l *qt4*
Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé/W=attend-traitement-déclenchements
|/ Err?=(aucune)/besoin Réinstallation (État,Err: majuscule=mauvais)
||/ Nom               Version           Description
+++-=================-=================-==================================================
un  ibus-qt4          <néant>          (aucune description n'est disponible)
ii  libqt4-assistant  4:4.6.2-0ubuntu5  Qt 4 assistant module
un  libqt4-core       <néant>          (aucune description n'est disponible)
ii  libqt4-dbus       4:4.6.2-0ubuntu5  Qt 4 D-Bus module
ii  libqt4-designer   4:4.6.2-0ubuntu5  Qt 4 designer module
un  libqt4-dev        <néant>          (aucune description n'est disponible)
un  libqt4-gui        <néant>          (aucune description n'est disponible)
ii  libqt4-help       4:4.6.2-0ubuntu5  Qt 4 help module
ii  libqt4-network    4:4.6.2-0ubuntu5  Qt 4 network module
ii  libqt4-opengl     4:4.6.2-0ubuntu5  Qt 4 OpenGL module
un  libqt4-phonon     <néant>          (aucune description n'est disponible)
un  libqt4-phonon-dev <néant>          (aucune description n'est disponible)
ii  libqt4-script     4:4.6.2-0ubuntu5  Qt 4 script module
ii  libqt4-scripttool 4:4.6.2-0ubuntu5  Qt 4 script tools module
ii  libqt4-sql        4:4.6.2-0ubuntu5  Qt 4 SQL module
ii  libqt4-sql-mysql  4:4.6.2-0ubuntu5  Qt 4 MySQL database driver
un  libqt4-sql-odbc   <néant>          (aucune description n'est disponible)
un  libqt4-sql-psql   <néant>          (aucune description n'est disponible)
ii  libqt4-sql-sqlite 4:4.6.2-0ubuntu5  Qt 4 SQLite 3 database driver
un  libqt4-sql-sqlite <néant>          (aucune description n'est disponible)
ii  libqt4-svg        4:4.6.2-0ubuntu5  Qt 4 SVG module
ii  libqt4-test       4:4.6.2-0ubuntu5  Qt 4 test module
ii  libqt4-webkit     4:4.6.2-0ubuntu5  Qt 4 WebKit module
ii  libqt4-xml        4:4.6.2-0ubuntu5  Qt 4 XML module
ii  libqt4-xmlpattern 4:4.6.2-0ubuntu5  Qt 4 XML patterns module
ii  python-qt4        4.7.2-0ubuntu1    Python bindings for Qt4
un  python-qt4-common <néant>          (aucune description n'est disponible)
un  python-qt4-dbg    <néant>          (aucune description n'est disponible)
ii  python-qt4-dbus   4.7.2-0ubuntu1    DBus Support for PyQt4
un  python-qt4-dev    <néant>          (aucune description n'est disponible)
un  python2.6-qt4     <néant>          (aucune description n'est disponible)
un  python2.6-qt4-dbu <néant>          (aucune description n'est disponible)
un  qt4-designer      <néant>          (aucune description n'est disponible)
un  qt4-qtconfig      <néant>          (aucune description n'est disponible)
```

---

### Post by lithium_hydride on 2010-09-27
I've just bought an HP Deskjet F2480 and had a similar problem. The solution for me was to install python-qt4.

---

### Post by Bob Morane on 2010-09-28
Hello, i just found the solution to my own issue in another thread. Iactually had all the required packages. The issue was a broken dependency in some qt4 lib after installing the official beid middleware (application for reading belgium elctronic ID card). I had to install the package provided by the federal government as my ID card was too recent for the ubuntu package, but the official package broke some QT4 lib.

[Full solution here]("http://ubuntuforums.org/showthread.php?t=1469364")

Going to solved status now.

---

