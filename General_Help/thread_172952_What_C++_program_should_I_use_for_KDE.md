---
title: "What C++ program should I use for KDE?"
date: 2006-05-09
forum: General Help
---

### Post by Christmas on 2006-05-09
I need a C++ development environment for KDE in order to study C++. Back in GNOME I was using Anjuta but it looks like the needed libraries are not installed or whatever. So what KDE-based program would you recommand?

---

### Post by ComplexNumber on 2006-05-09
try kdevelop [here]("http://www.kdevelop.org/") and qdesigner which comes with the qt packages. kdevelop will be available in the repositories and is part of kde-sdk.

---

### Post by GoldBuggie on 2006-05-09
Kdevelop or kate.
kdevelop for a bigger suit with projects and such(more visual studio like).
kate for a highlighting syntax editor with nice konsole integration for gcc usage.

---

### Post by Christmas on 2006-05-11
Well I installed KDevelop and I made a simple C "Hello World" program to test it. But at the Build menu I have only the stop option which is not active. When I press on the build menu the program does nothing. How can I compile with KDevelop anyone pls help?

LE: I forgot to mention, I only need a simple C++ compiler for studying C++, not a complete developing studio. However if KDevelop makes it then I'm going to use it.

---

### Post by Luke on 2006-05-11
i don't know if this addresses the problem you are describing but when i installed kdevelop, i also had to install libtools

[COLOR="Blue"]sudo apt-get install libtools[/COLOR]

---

### Post by mexlinux on 2006-05-11
You might also need to install build-essentials

---

### Post by Christmas on 2006-05-12
Ok thanks guys I'm on a Debian system right now but I'll try once I get Kubuntu.

---

### Post by Luke on 2006-05-12
[QUOTE=mexlinux]You might also need to install build-essentials[/QUOTE]
good point. for some reason i assumed the OP already had that but that may not be the case.

---

### Post by jferrando on 2006-05-12
If you want to learn kde, you must start learning qt.
Go to the web page [http://www.trolltech.com]("http://www.trolltech.com")
 and search the qt documentation.
[http://doc.trolltech.com]("http://doc.trolltech.com")
After that you can start learning KDE.
The C++ IDE is kdevelop.
I only program cross-platform qt, never used kdevelop, I still use kate or other editors and command line.
You can check my notes about qt installation in spanish
[http://www.intransys.com/linux/qt/NotasProgramacionQt4.odt]("http://www.intransys.com/linux/qt/NotasProgramacionQt4.odt")

---

### Post by Christmas on 2006-05-12
Thanks all for your help I found a simpler solution. I'll just edit my c/c++ files with nano or kate and compile them in the Konsole with gcc or g++. This is just as simple as I needed it to be and does my job greatly. Thanks again all.

---

