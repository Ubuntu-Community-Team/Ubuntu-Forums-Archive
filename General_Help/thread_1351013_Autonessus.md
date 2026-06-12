---
title: "Autonessus"
date: 2009-12-09
forum: General Help
---

### Post by serialfish on 2009-12-09
I installed AutoNessus and the dependencies were fine. Everything seems as if it has installed properly, yet I don't see it in the Applications Menu.

Has this happened to anyone else? How did you fix it? If not, is there any standard process for programs that seem to have installed correctly, yet don't appear in the Menu after installation?

---

### Post by 3rdalbum on 2009-12-10
I can't find this package in the repositories.

If the program is a command-line program, then it won't appear in the menu. You can find it by selecting the package in Synaptic, right-clicking, going to Properties and then over to the "Installed Files" tab. The files inside /bin, /usr/bin, /sbin are executable and you need only type the name.

For instance, if the package contains /usr/bin/autonessus, then you just need to type "autonessus" in the command-line.

Some programs are just daemons, they start when the computer does (actually, they start as soon as the package gets installed). They usually also install some sort of remote control program (command-line) as well so you can restart the daemon or force it to reload its configuration file. For daemons, of course, you won't see their icon in the Applications menu, and unless their remote control program is a GUI one you won't see that in the menu either.

The usual procedure with these is to look at the man page (try "man autonessus" or "man -k autonessus") and find where the configuration file gets stored, and then edit it and restart the daemon with the remote control program.

---

### Post by Seccubus on 2009-12-13
> **serialfish said:**
> I installed AutoNessus and the dependencies were fine. Everything seems as if it has installed properly, yet I don't see it in the Applications Menu.

Has this happened to anyone else? How did you fix it? If not, is there any standard process for programs that seem to have installed correctly, yet don't appear in the Menu after installation?

I am the author of AutoNessus (currently called Seccubus) but I wasn't ware that there was an Ubuntu package for it. 
Normally AutoNessus should create a user called autonessus, can you do an 'ls ~autonessus' and post the results?

---

