---
title: "How to run GParted?"
date: 2009-10-03
forum: General Help
---

### Post by isee on 2009-10-03
Hello,

Can't believe I can't find it myself, but I've enabled GParted with Synaptic because I want to create a partition, but I can't find how to access it.

A sudo command would do fine.

Thanks!
Roland

---

### Post by drs305 on 2009-10-03
> **isee said:**
> Hello,

Can't believe I can't find it myself, but I've enabled GParted with Synaptic because I want to create a partition, but I can't find how to access it.

A sudo command would do fine.

Thanks!
Roland

```
gksu gparted
```
or 
System, Administration, Partition Editor
or 
System, Administration, Gparted (Karmic Beta)


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by isee on 2009-10-03
errrr....   I mean a Terminal command.:oops:

Thanks much!

---

### Post by oboedad55 on 2009-10-03
> **isee said:**
> errrr....   I mean a Terminal command.:oops:

Thanks much!

Dude, that's what he gave you here: 

Code:
gksu gparted

Copy/paste it into the terminal.

---

### Post by isee on 2009-10-03
lol  ya I've since been informed.  I didn't know that gksu was short for gksudo.  First experience with that command.

---

### Post by oboedad55 on 2009-10-04
> **isee said:**
> lol  ya I've since been informed.  I didn't know that gksu was short for gksudo.  First experience with that command.

Okay, cool. You can use it to start up nautilus as super-user. gksu nautilus.

---

