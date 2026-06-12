---
title: "Could not open lock file /var/lib/apt/lists/lock"
date: 2006-02-19
forum: General Help
---

### Post by aljones15 on 2006-02-19
Tried searching for this. When i run apt-get update get the following error:

 apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


I searched around and found a few posts explaing dpkg lock, but how do I get rid of this problem and let apt-get update?

Also, I've posted several times about my video card problems. When I go to uninstall the ati drivers it wants to uninstall my xwindows system core. how do I uninstall the ati drivers and install the right video drivers with out possibly ruining my copy of ubuntu?

thanks,
A

---

### Post by heimo on 2006-02-19
[quote=aljones15]Tried searching for this. When i run apt-get update get the following error:

 apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
[/quote]

```
sudo apt-get update
```

---

### Post by kingsidy on 2006-02-19
you need to run it as root as heimo suggested. sudo apt-get update

---

### Post by shade11 on 2006-02-19
Anything apt-get'ed or dpkg'ed needs to be run as su, root, or sudo.

So when apt-get'ing something it would be

sudo apt-get install whateverapp

---

### Post by aljones15 on 2006-02-19
[QUOTE=heimo]```
sudo apt-get update
```[/QUOTE]
yeah I've done that before. this time around when i open
synaptic package manager afterwords it works so thanks.

-
A

---

