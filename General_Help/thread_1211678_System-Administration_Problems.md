---
title: "System-Administration Problems"
date: 2009-07-12
forum: General Help
---

### Post by Squegee on 2009-07-12
I just got a new printer and I am trying to configure it when I found out that I am missing the tool in the system-administration menu that configures printers, the *Printing* tool. After a little research I found out that I am missing some other applications that are supposed to be in the administration menu. I was wondering how I can install the proper applications. The main tools im missing is of course the *Printing* tool and then the *Login Screen Setup* tool. Any help is appreciated.

---

### Post by seventyeights on 2009-07-12
Try Preferences/Main-Menu to see if your applications are simply deselected from showing in the menu.

Or run terminal and try them directly:

for the printing manager:
gksudo system-config-printer

for the login manager:
gksu /usr/sbin/gdmsetup

if you are missing the menu editor:
alacarte

if you are also missing the terminal:
Alt F2

---

### Post by Squegee on 2009-07-13
I didn't have the Printer application deselected, and when I ran 
gksudo system-config-printer
Nothing happens, but it said I needed to install the correct package so I did and now I have the correct application, but the printer doesn't work, but that is for another forum.
Thanks for your help

---

