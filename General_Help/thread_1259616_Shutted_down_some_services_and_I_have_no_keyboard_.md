---
title: "Shutted down some services and I have no keyboard or mouse"
date: 2009-09-06
forum: General Help
---

### Post by alek66 on 2009-09-06
In a follish attempt to free more ram with less programs running I shutted down some services (cron, acron, logs ..some more I cant remember) I after rebooting I dont have keyboard and mouse.

Any help to restore this basic functions would be great!!!
thx

---

### Post by Lampi on 2009-09-06
boot the live cd and mount the partition, then have a look at your bash history file (.bash_history) placed in the home directory - if you shut down a few services (maybe udev?) you will find them in the history and add them to the runlevels again

---

### Post by alek66 on 2009-09-08
how do I add the servies to the run levels?
besides i did it with a gnome administration tool... so history shows...nothing about it..

anyway how do I add udev to runlevel.

is there a way to restablish the default services again?

cheers

---

### Post by Lampi on 2009-09-09
Don't know about this gnome tool, I use sysv-rc-conf or update-rc.d to manage runlevels from a terminal. You could check for a logfile/history in this gnome administration tool you used.

> **alek66 said:**
> 
anyway how do I add udev to runlevel.
here's how it's done in a terminal:
```
sudo update-rc.d udev defaults
```
> **alek66 said:**
> 
is there a way to reestablish the default services again?
I wouldn't know  - don't think so.

---

