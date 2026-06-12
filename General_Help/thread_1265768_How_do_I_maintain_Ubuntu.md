---
title: "How do I maintain Ubuntu?"
date: 2009-09-13
forum: General Help
---

### Post by Ubu4moi on 2009-09-13
What do I do to clean up the OS of temporal files and clear of the old "open with" items that are no longer available, etc.? Is there an app to do all sorts of maintenance tasks?

---

### Post by pythonscript on 2009-09-13
Some basic clean up tips:

```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean

```

Also, install deborphan:
```
sudo apt-get install deborphan -y
```

then run:

```
sudo deborphan | xargs sudo apt-get purge -y
``` to clean up any old packages on your system that might not have been removed by apt-get autoremove. Finally, run:

```
dpkg-query -W -f='\''\t\n'\'' | awk '\''/deinstall/{print }'\''
```, which will display a list of all packages left over that have "residual configs." Use this command, followed by
```
| xargs sudo apt-get purge -y
```. These are all a good place to start in cleaning up your system.

---

### Post by fooman on 2009-09-13
bleachbit will do at least some of what you want...find it in synaptic,  or open a terminal and type or copy/paste the following:

```
sudo apt-get install bleachbit
```

---

### Post by pythonscript on 2009-09-13
> **fooman said:**
> bleachbit will do at least some of what you want...find it in synaptic,  or open a terminal and type or copy/paste the following:

```
sudo apt-get install bleachbit
```

Wow... I completely forgot about this tool. Nice tip. +1 on this, definitely.

---

### Post by steveneddy on 2009-09-13
Those are great answers

---

### Post by Ubu4moi on 2009-09-13
> **pythonscript said:**
> Wow... I completely forgot about this tool. Nice tip. +1 on this, definitely.
bleachbit doesn't seem to be available anymore :(

---

### Post by Ubu4moi on 2009-09-13
What does the -y in install stand for?

---

### Post by Andrew.Z on 2009-09-14
> **fooman said:**
> bleachbit will do at least some of what you want...find it in synaptic,  or open a terminal and type or copy/paste the following:

```
sudo apt-get install bleachbit
```

The BleachBit version in the Ubuntu 9.04 repository (BleachBit version 0.3.1) is old and buggy. The new version is much better.  There are .deb packages on the official [BleachBit web site](http://bleachbit.sourceforge.net/).

---

### Post by misfitpierce on 2009-09-14
Indeed Bleachbit for freeing up space is a awesome tool.

---

### Post by ankspo71 on 2009-09-14
-y in a command line means "do it without asking for my permission about dependencies or whatever"

---

