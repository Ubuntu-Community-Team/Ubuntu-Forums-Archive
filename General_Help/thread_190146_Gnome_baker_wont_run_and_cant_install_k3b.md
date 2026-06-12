---
title: "Gnome baker wont run and cant install k3b"
date: 2006-06-05
forum: General Help
---

### Post by wswswsws on 2006-06-05
Hi, i installed gnome baker via add/remove but it wont run. (the window comes up but with nothing in it and i have to force quit)

also tried installing k3b via add/remove but it says theres a conflict and cant install?

nero anyone:P?


EDIT: Not to worry, i got nerolinux installed

---

### Post by Brunellus on 2006-06-05
what kind of conflict are you seeing?  paste the full text of the error here.

---

### Post by professor_chaos on 2006-06-06
I dont know about your gnome baker problem, but for k3b...
what is the output when you type this.

```
sudo apt-get install k3b
```

---

### Post by wswswsws on 2006-06-06
[QUOTE=Brunellus]what kind of conflict are you seeing?  paste the full text of the error here.[/QUOTE]

Cannot install 'k3b'

This application conflicts with other installed software. To install 'k3b' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.

*********************************************************
*********************************************************

[QUOTE=professor_chaos]I dont know about your gnome baker problem, but for k3b...
what is the output when you type this.[/QUOTE]


john@john-desktop:~$ sudo apt-get install k3b
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  k3b: Depends: k3blibs (>= 0.12.2) but it is not going to be installed
       Depends: kdelibs4c2 (>= 4:3.4.2) but it is not going to be installed
       Depends: libdbus-1-1 (>= 0.36.2) but it is not going to be installed
       Depends: libdbus-qt-1-1c2 (>= 0.36.2) but it is not going to be installed       Depends: libmusicbrainz4c2 (>= 2.1.1) but it is not going to be installed       Depends: kdebase-bin but it is not going to be installed
       Depends: kcontrol but it is not going to be installed
E: Broken packages


*********************************************************
*********************************************************


EDIT: Its really a moot point for me, because iv got nero linux running with my windoze serial. (unless theres stuff k3b can do that nero cant)

thanks as ever

---

