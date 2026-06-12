---
title: "Suspend not working propertly on ubuntu 9.04"
date: 2009-08-02
forum: General Help
---

### Post by Zoyberk on 2009-08-02
Hello, 

I'v been using kubuntu for a while and now switched to ubuntu, 
when i first installed kubuntu on my laptop suspend(sleep) function worked well,
but when i reinstalled kubuntu for some reasons sleep function stopped to work.
Switched to ubuntu (installed gnome and deleted all what is kde) and i have same problem:
When i put computer to suspend it suspend properly but then 
[LEFT]immediately wake up agen.
 
So how to fix that cuz its very annoying since i cant put laptop to sleep :D
[/LEFT]

---

### Post by sigixv on 2009-08-02
[http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html](http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html)
[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)
[http://ubuntuforums.org/showthread.php?t=417964&page=2](http://ubuntuforums.org/showthread.php?t=417964&page=2)

the first 2 are basically the same...

---

### Post by Zoyberk on 2009-08-02
s2disk works fine(like it used to) but when s2ram i get this:
```
zoyberk@zoyberkolandija:~$ sudo s2ram
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "Acer            "
    sys_product  = "Aspire 5737Z    "
    sys_version  = "V1.06"
    bios_version = "V1.06"
See http://suspend.sf.net/s2ram-support.html for details.

If you report a problem, please include the complete output above.

```

---

### Post by Zoyberk on 2009-08-09
anyone? ...cuz i realy want sleep function

---

### Post by P4man on 2009-08-09
As it says, your machine is unknown.. From the link included in your output: 

> The best way to start investigating an unknown machine is probably to boot with init=/bin/bash at the boot prompt into a minimal environment, then do:

 # mount /proc
 # mount /sys
 # s2ram -f

if the first try already succeeds, everything is fine. Send us the output of s2ram -i, and don't forget to mention that plain s2ram -f was enough even from text mode (see #How to contact the authors of s2ram?). If it doesn't, try the following variations:

    * s2ram -f -a 3
    * s2ram -f -a 2
    * s2ram -f -a 1
    * s2ram -f -p -m
    * s2ram -f -p -s
    * s2ram -f -m
    * s2ram -f -s
    * s2ram -f -p
    * s2ram -f -a 1 -m
    * s2ram -f -a 1 -s 

If none of those combinations work, start again but add the "-v" switch. 

Read the rest of the page too.

Then contact the authors to let hem know your findings

---

