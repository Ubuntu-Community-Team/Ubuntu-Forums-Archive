---
title: "No Synaptic or Terminal"
date: 2010-07-25
forum: General Help
---

### Post by Ted3929 on 2010-07-25
Something went horribly wrong yesterday after installing Google Earth.  During the process something happened and the computer shut down before it was completely installed.

Now I can't access Terminal, Synaptic Package Manager or Add/Remove, nor can I access Google Earth.  All other programs work but these will not.

Anybody have a clue what to do?  Please keep in mind I can't access Terminal, Package Manager or Add/Remove to enter commands.

Thanks

---

### Post by SlidingHorn on 2010-07-25
never heard of not having access to terminal...have you tried booting in recovery mode and running an apt-get update/upgrade?  Do you receive any error messages?

Also, how are you trying to open it?  via menu?  what happens if you try Alt+F2 and enter

```
gnome-terminal
```

---

### Post by Ted3929 on 2010-07-25
I got terminal back by scaling back graphics to none because some forums show a problem with that area, but updating, add/remove and synaptic are still gone.

---

### Post by SlidingHorn on 2010-07-25
in your terminal try running the following:

```
sudo apt-get update

sudo apt-get upgrade
```

---

### Post by Ted3929 on 2010-07-25
get a segmentation faulty tree warning at 1% on the upgrade and then it either completely locks up the unit or crashes

---

### Post by SlidingHorn on 2010-07-25
there are a couple suggestions in here that have worked for folks in the past.  It's for an older version of Ubuntu though.

[http://ubuntuforums.org/showthread.php?t=773787](http://ubuntuforums.org/showthread.php?t=773787)

---

