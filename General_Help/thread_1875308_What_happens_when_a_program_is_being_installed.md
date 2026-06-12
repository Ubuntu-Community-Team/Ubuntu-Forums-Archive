---
title: "What happens when a program is being installed?"
date: 2011-11-04
forum: General Help
---

### Post by lovabill on 2011-11-04
In Windows the installation does this:
-copy/extract files in c:/program files/program name
-register a thousand registry entries
-creates a shortcut in c:/users/username/app data/....(etc)

What happens in Ubuntu? For example when we install VLC via software center, what happens? Binary files go to usr, library files in lib, and a shortcut somewhere?

Thanx if anyone responds.

---

### Post by hwttdz on 2011-11-04
Perhaps you'd be interested to right click on an installed package (like vlc) in synaptic->properties->installed files.
That will give you an idea of some things that might get placed on your filesystem.  It is also possible to add or remove lines from scripts when a package is installed or uninstalled.  Some of them will schedule a daemon to run on certain runlevels, or load kernel modules on boot.  There are a lot of possibilities.  I rather like that they're relatively transparent, and though it's not frequently I look at what they're doing it's nice to be able to determine it if I need to.

---

### Post by Lars Noodén on 2011-11-04
I can't find a non-technical overview of either [APT](http://manpages.ubuntu.com/manpages/oneiric/en/man8/apt.8.html) or [dpkg](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html), it would be nice if one existed.  So you'll have to look around yourself for APT and wade through what you find.  

Maybe a good place to start is with [Secure APT](http://wiki.debian.org/SecureApt)

At least you can see the files that are in a package by searching Ubuntu's online package database:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by lovabill on 2011-11-05
Thank you! Found enough for my curiosity.

---

