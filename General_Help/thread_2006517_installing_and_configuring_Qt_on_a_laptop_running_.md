---
title: "installing and configuring Qt on a laptop running Ubuntu 12.04"
date: 2012-06-19
forum: General Help
---

### Post by modoM0jo on 2012-06-19
Hi. I'm having trouble installing Qt onto my ubuntu laptop which is running Precise Pangolin.

I think I may have to reinstall it via synaptic or apt-get. What packages do I need to install for Qt?

The problem is that during compilation the compiler fails to find header files like QDebug. It also returns a linking error as it is unable to find QtGui or QtCore. I think that this may have resulted from the installation process. Is there something I can do to reconfigure Qt or some other way to install it so that 'make' can find all the header files and linked libraries? Much in need of help. 

I have been told I need to install from the system repositories. Could you tell me which packages to install?

---

### Post by kc1di on 2012-06-19
I guess I'm at a loss to figure out why your trying to install QT from sources. It's in the repositories and can be installed from there. 

But the easiest way to get all the qt you need would be to install kubuntu-desktop. That will pull qt and install it for you. 

If there is a specific program your trying to install that require qt it should pull the dependencies it needs from the repositories.

Qt is normally associated with kde pacakages. and gtk normally with gnome and xfce packages. but can be run in either enviroment.

Let us know what your trying to do in the end and we can be of more help. 

normally when your compiling form source code you need to have all the dependencies met already on your machine before you compile.  That is if you want to compile qt - you will have to get a list of it's dependencies , which is quite long and build and install them first.  It can be very time consuming to track down and install each one from source.

good luck

---

### Post by 3Miro on 2012-06-19
QT has many components and it depends on which components you need. Install Synaptic Package Manager and use it to search for packages called QT. If you want to just run QT programs you only need to install the program itself as it will pull all the needed packages automatically. If you want to write QT programs, then you will need the dev packages.

---

