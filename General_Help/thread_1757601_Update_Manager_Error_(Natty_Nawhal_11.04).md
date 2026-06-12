---
title: "Update Manager Error (Natty Nawhal 11.04)"
date: 2011-05-13
forum: General Help
---

### Post by skaddict on 2011-05-13
So I was messing around with some stuff I probably shouldn't have when trying to get my Intel graphics card working better (that's another problem completely). Now the update manager has ceased to work. Every time I try to use it this error pops up:

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu' is not known on line 57 in source list /etc/apt/sources.list'

Any help would be greatly appreciated as I am a complete "noob" when it comes to this kind of thing.

---

### Post by TeoBigusGeekus on 2011-05-13
Fire up a text editor with root priviledges
```
gksu gedit /etc/apt/sources.list
```
and comment out/delete line 57 - the one that has the string
```
http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu
```
in it.

---

### Post by skaddict on 2011-05-13
Thanks! Worked like a charm, I thought about deleting that line but didn't want to mess it up more. Thanks again!

---

