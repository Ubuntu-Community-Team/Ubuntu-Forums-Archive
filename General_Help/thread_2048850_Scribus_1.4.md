---
title: "Scribus 1.4"
date: 2012-08-27
forum: General Help
---

### Post by pelDK on 2012-08-27
When I try to get Scribus 1.4 to get or store on the hard disk, I get:
Scribus crashes due to Signal #6
I use Ubuntu 12.04.

Sincerely,
pelDK

---

### Post by Buntu Bunny on 2013-04-24
OK. I'm having this problem too. I get a signal #6 error when I try to import text from LibreOffice. When I click okay, Scribus closes itself out. Does anyone have a clue?

---

### Post by tgalati4 on 2013-04-24
Can you open Scribus within a terminal to see if there are any messages?

---

### Post by Buntu Bunny on 2013-04-24
> **tgalati4 said:**
> Can you open Scribus within a terminal to see if there are any messages?

Thank you for responding tgalati4. Scribus opens via terminal and gives me this

```
Got bus address:  "unix:abstract=/tmp/dbus-8hUS6iPVRP,guid=a5b03b0f08d9a9fac59967dc00000021" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-8hUS6iPVRP,guid=a5b03b0f08d9a9fac59967dc00000021" 
Registered DEC:  true 
```

After the crash, I get this

```

Registered event listener change listener:  true 
QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0x1fe16d0) "" 
QSpiAccessible::accessibleEvent not handled:  "7"  obj:  QMenu(0x1fe16d0) "" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
QSpiAccessible::accessibleEvent not handled:  "6"  obj:  ContextMenu(0x2773990) "" 
QSpiAccessible::accessibleEvent not handled:  "7"  obj:  ContextMenu(0x2773990) "" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QSidebar(0x2794da0, name = "sidebar") "sidebar" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
FIXME: handle dialog start. 
FIXME: handle dialog start. 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QListView(0x2951650, name = "listView") "listView" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
Interface is not valid 
ASSERT failure in : "Got an update for an invalid inteface. Investigate this.", file atspiadaptor.cpp, line 899
Scribus Crash
-------------
Scribus crashes due to Signal #6
QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0x7fff8d0fb440) "" 
FIXME: handle dialog start. 
QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0x277ef70) "" 
QSpiAccessible::accessibleEvent not handled:  "7"  obj:  QMenu(0x277ef70) "" 

```
.

---

### Post by Buntu Bunny on 2013-04-25
Today it's crashing due to signal #11. In addition, Ubuntu detected it and created a crash report. Progress???

I tried to replicate this from terminal, but it reverted to the same problem as yesterday, crashing due to signal #6 when I tried to import text into a text frame (no detection or report generated).

```
Got bus address:  "unix:abstract=/tmp/dbus-XvX9NIv5kt,guid=c770048f47f0dfd00591b48d0000002d" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-XvX9NIv5kt,guid=c770048f47f0dfd00591b48d0000002d" 
Registered DEC:  true 
Registered event listener change listener:  true 
QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0x29855b0) "" 
QSpiAccessible::accessibleEvent not handled:  "7"  obj:  QMenu(0x29855b0) "" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
QSpiAccessible::accessibleEvent not handled:  "6"  obj:  ContextMenu(0x2c799d0) "" 
QSpiAccessible::accessibleEvent not handled:  "7"  obj:  ContextMenu(0x2c799d0) "" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QSidebar(0x366bf00, name = "sidebar") "sidebar" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
FIXME: handle dialog start. 
FIXME: handle dialog start. 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QListView(0x3583130, name = "listView") "listView" 
QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
Interface is not valid 
ASSERT failure in : "Got an update for an invalid inteface. Investigate this.", file atspiadaptor.cpp, line 899
Scribus Crash
-------------
Scribus crashes due to Signal #6
QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0x7fffd97e3280) "" 
FIXME: handle dialog start. 
FIXME: handle dialog end. 
Calling Emergency Save
```

I don't understand the above code, except that something is not handled and an interface is invalid. I just wish I knew what to do about it. Any ideas?

---

### Post by Buntu Bunny on 2013-04-25
Solved, but since I didn't start the thread I can't mark it as such. 

The solution is to remove the package qt-at-spi. That fixes the problem and stops the crashes.

---

### Post by tgalati4 on 2013-04-25
I was going to say it looks like a conflict with some Accessibility function.  If you have accessibility turned on or if you are using it on another application then that *qt-at-spi* package gets installed.

tgalati4@Mint14-Extensa ~ $ apt-cache search "qt-at-spi"
qt-at-spi - accessibility plugin for Qt

---

### Post by Buntu Bunny on 2013-04-25
> **tgalati4 said:**
> I was going to say it looks like a conflict with some Accessibility function.  If you have accessibility turned on or if you are using it on another application then that *qt-at-spi* package gets installed.


You know, when I first installed Xubuntu, I was looking through the menus and found Orca. I didn't know what it was so clicked on it, to check it out. It activated and I never could figure out how to turn it off. I reckon removing qt-at-spi took care of that too!

---

### Post by tgalati4 on 2013-04-25
Yes, Orca is an accessibility package, but it does not appear to use qt-at-spi:

tgalati4@Mint14-Extensa ~ $ apt-cache depends gnome-orca
gnome-orca
  Depends: python3
  Depends: python3-speechd
  Depends: python3-gi
  Depends: python3-pyatspi2
  Depends: python3-cairo
  Depends: python3-brlapi
  Depends: python3-louis
  Depends: gir1.2-glib-2.0
  Depends: gir1.2-pango-1.0
  Depends: gir1.2-gtk-3.0
  Depends: gir1.2-wnck-3.0
  Conflicts: <gnome-orca-common>
  Conflicts: <gnome-orca-common:i386>
  Replaces: <gnome-orca-common>
  Replaces: <gnome-orca-common:i386>

So, some other package must have installed it.

---

### Post by Buntu Bunny on 2013-04-26
> **tgalati4 said:**
> Yes, Orca is an accessibility package, but it does not appear to use qt-at-spi: ..... So, some other package must have installed it.

That's interesting because Orca was specifically mentioned at the site I found the fix. Well, I'm clueless, but at least you've given me good information so I'll have a heads up in the future. I appreciate your help. Thanks Tgalati4!

---

### Post by tgalati4 on 2013-04-26
It's possible that one of orca's dependencies rely on it.  I didn't check them.

---

