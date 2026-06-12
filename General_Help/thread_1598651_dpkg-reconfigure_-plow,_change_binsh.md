---
title: "dpkg-reconfigure -plow, change /bin/sh"
date: 2010-10-16
forum: General Help
---

### Post by legendbb on 2010-10-16
One installation requires shell change from /bin/sh -> dash to -> bash

Suggested using: [COLOR=DarkRed]$ sudo dpkg-reconfigure -plow dash[/COLOR]

could not find -plow option in the dpkg-reconfigure man, don't understand this arguments,

Can anyone point me to the right reference for the actual meaning, 

Thanks,

---

### Post by dcstar on 2010-10-16
> **legendbb said:**
> One installation requires shell change from /bin/sh -> dash to -> bash
........
```
sudo dpkg-reconfigure debconf
```
Select Gnome, then:
```
sudo dpkg-reconfigure dash
```
and untick the box.

---

### Post by chrisstankevitz on 2011-01-03
> **legendbb said:**
> 
Suggested using: [COLOR=DarkRed]$ sudo dpkg-reconfigure -plow dash[/COLOR]

could not find -plow option in the dpkg-reconfigure man, don't understand this arguments

I agree.  Can someone explain what "-plow" does?

Thank you,

Chris

---

### Post by Pilo on 2012-11-11
Sorry to resurrect an old thread, but I had the same question.  

After staring at the man page for a while, I realized that '-plow' was just the short form of '--priority=low'.
That is, show all questions of 'low' priority or higher.

---

