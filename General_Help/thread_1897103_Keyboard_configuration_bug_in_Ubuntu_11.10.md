---
title: "Keyboard configuration bug in Ubuntu 11.10"
date: 2011-12-18
forum: General Help
---

### Post by ubix on 2011-12-18
I am running ***»Ubuntu 10.10 Maverick«*** on a home built AMD hardware. I have a slick aluminium Apple keyboard connected to it. I can configure Ubuntu to recognize this keyboard by placing into **/etc/rc.local**  the following line: 

```
echo 2 > /sys/module/hid_apple/parameters/fnmode
```

However, I am also running ***»Ubuntu 11.10 Oneiric«*** in a VirtualBox on Apple. Trying to configure Ubuntu to recognize Apple keyboard there fails! Namely, in ***_Ubuntu 11.10 Oneiric_*** the special directories **hid_apple/parameters** and the function key parameter file **fnmode** are now (*in **11.10***)  missing in **/sys/module/** hierarchy, and indeed, can not be created because these are special files!

Is there a chance that this will get fixed :?

> **Sub-NOTE:**
Since at first I didn't know which forum would be the best to publish my concerns about the latest Ubuntu bug regarding the configuration of Apple keyboards, I have posted similar threads to this one in three different forums:

[LIST]
[*]Installation & Upgrades
[*]Hardware & Laptops
[*][Apple Users](http://ubuntuforums.org/showthread.php?p=11545699#post11545699)
[/LIST]
but and the maintainers removed it from all but the ***»Apple users«***. I have to object to this, since it does not pertain only to users of Virtual Machines on Apple running Ubuntu, but also to Ubuntu users on regular PC's and/or home built Intel or AMD boxes, which happen to be using Apple keyboards. 

---

### Post by lisati on 2011-12-18
Please choose the appropriate forum for your support threads and post only one thread per support issue.

---

### Post by ubix on 2011-12-20
I was hoping someone from Ubuntu will be able to tell us, what happened. I believe, this issue should be addressed sooner or later.

---

