---
title: "My installed software missing from applications menu."
date: 2010-07-15
forum: General Help
---

### Post by ChuckyZ28 on 2010-07-15
I have downloaded a couple of software packages from the ubuntu software center and they are not showing up in the applications menu on top, I have no idea where on the hard drive it stores them so I can find them manually and place a shortcut in the applications menu.

---

### Post by drs305 on 2010-07-15
If you provide the names of the apps we can probably help you out. 

From a terminal, if you know the app's name, you may be able to use the following to find the executable:
```
which <appname>
```
The problem is that if you know the executable name you probably wouldn't have to post here. ;-)  Don't forget though that in a terminal you can type the first part of the name and then double-tab to see the possibilities. For instance, typing "which gi" and double tabbing will provide various *gimp* possibilities.

You could also check the dpkg logs via System, Administration, Log File Viewer to see what was just installed (/var/log/**dpkg.log** or perhaps /var/log/**aptitude**).

---

### Post by 3rdalbum on 2010-07-15
Locate the packages in Synaptic Package Manager , right click them and choose "Properties" and then go to the Installed Files tab. Anything inside a directory with the name "bin" is a program that can be run.

If the program has not gone into your Applications menu it usually means that it's a command-line (terminal) program and does not have a GUI, but there are a couple of exceptions to this.

---

### Post by ChuckyZ28 on 2010-07-15
> **drs305 said:**
> If you provide the names of the apps we can probably help you out. 

From a terminal, if you know the app's name, you may be able to use the following to find the executable:
```
which <appname>
```The problem is that if you know the executable name you probably wouldn't have to post here. ;-)  Don't forget though that in a terminal you can type the first part of the name and then double-tab to see the possibilities. For instance, typing "which gi" and double tabbing will provide various *gimp* possibilities.

You could also check the dpkg logs via System, Administration, Log File Viewer to see what was just installed (/var/log/**dpkg.log** or perhaps /var/log/**aptitude**).

I did that and it is not able to locate, Could this mean its a bad installer on the software center or possibly its not compatible with my OS Verson?

EDIT: Disregard It is now showing up in the menu after restarting the computer.

---

### Post by dcollier on 2010-07-15
Just type the name of the application that you installed at the command line and press enter.  If the application is installed properly it should launch the application.  If it errors then reinstall the application.

---

