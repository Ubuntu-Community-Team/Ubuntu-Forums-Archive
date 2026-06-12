---
title: "I just install a program. I can't find it to run it"
date: 2010-06-21
forum: General Help
---

### Post by mobiblu on 2010-06-21
Can someone please explain the filing scheme of Ubuntu to me. In Windows/Mac, when I install a program/app, there a default folder (Program Files/App). I can't find the equivalent in Ubuntu. When I install program from the repository, where does it get install to? where do I go to run the program? Someone throw me a light. Thanks in advance

---

### Post by Autodave on 2010-06-21
> **mobiblu said:**
> Can someone please explain the filing scheme of Ubuntu to me. In Windows/Mac, when I install a program/app, there a default folder (Program Files/App). I can't find the equivalent in Ubuntu. When I install program from the repository, where does it get install to? where do I go to run the program? Someone throw me a light. Thanks in advance

First of all, did you look under APPLICATIONS ?  If not there, it is probably a program that needs run from a command line in a terminal window.  Your program should be in the directory  /usr/bin  .  In a terminal window, change to that directory and look for the executable and just type the name of it in the command line and hit ENTER.  You can also go to PLACES > COMPUTER > FILE SYSTEM > USR . BIN and find the file and click on it.

---

### Post by oldos2er on 2010-06-21
What program did you install? If it's CLI, no menu entry will be created, you just type the program name in a terminal to run it. ```
dpkg -L <package name>
``` will show you where each file in a package is installed.

---

### Post by yetiman64 on 2010-06-21
What is the program you installed? Usually an entry will be put in one of the many menus under "Applications", however if not it is very easy to make a launcher in there for it. 

First try in terminal 
```
<program name>
``` substitute this with the actual name of the program and see if it launches. If so it is easy to create a menu launcher for it as mentioned above.

Depends on the source of the program as to where it is installed, some possibilities (but not all by any means are):
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:
```taken from my system path, try.
```
echo $PATH
``` in terminal to see yours. (system path is where programs can be launched from with the terminal).

Another install path is /opt - binary packages like googleearth sometimes use this folder to install to.

---

### Post by Leppie on 2010-06-21
depends on what kind of application you installed, if it's something to do with system your app will go in System and then either Preferences or Administration, otherwise you should be able to find it under Applications.

if it's not at all in the menu, you could always launch it from a terminal.
normally executables are placed in /usr/bin, but not necessarily. you can find the application like this:
```
which <application-name>
```
so if i installed an application called underworld, i would find it like this:
```
which underworld
```

---

### Post by mobiblu on 2010-06-21
Thanks for all the feedback. To Autodave, yes I did looked under APPLICATIONS! It was the first place I looked. I just did know I could run program from terminal. Thanks again for the wealth of info.

---

