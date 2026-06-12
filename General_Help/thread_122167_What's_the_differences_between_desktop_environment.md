---
title: "What's the differences between desktop environment and windows manager?"
date: 2006-01-26
forum: General Help
---

### Post by tico on 2006-01-26
What's the differences between desktop environment (Gnome, KDE) and windows manager (Enlightenment, Windowmaker)?

TIA

---

### Post by Jedeye on 2006-01-26
Hi, this is my guess - the environment is made up of applications that you use and the manager renders all of the applications onto the screen.

---

### Post by Turtle.net on 2006-01-26
You can find first part of the answer there : 
[http://xwinman.org/intro.php](http://xwinman.org/intro.php)

---

### Post by az on 2006-01-26
A desktop environment glues together a bunch of different applications and services and gives them a framework to work under.  If you make an application for that environment, it will interact with other applications in that environment.

A window manager draws windows.  It takes care of placing the boxes on the screen.  It provides a few other tidbits like access to menus and some accessories.

A Display Manager manages different Desktop Environemtn sessions.  A desktop Environment needs a Window manager to display stuff. 

The Display manager runs on top of X.  That whole group of things is sometimes called "the stack", not to be comfused with "the stack" in memory management - how linux uses memory.

---

### Post by TecSoft on 2006-01-26
The diffrence is that a Desktop Enviroment has icons and its own suite of appliacations. A window manager does not. Fluxbox is a Window Manager, KDE and Gnome are Desktop enviorments.

---

### Post by Sutekh on 2006-01-26
[Ubuntu Forum - Window Managers for Beginners - by Kyral]("http://www.ubuntuforums.org/showthread.php?t=87276")

---

