---
title: "problem installing testdisk"
date: 2011-08-02
forum: General Help
---

### Post by esagherardo on 2011-08-02
Tried to install testdisk with synaptic. It hung at unpacking. Killed synaptic, removed lock, dpkg --configure -a, started again with apt-get, failed again.

Tried again dpkg --configure -a, then apt-get clean, then
```
# apt-get purge testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  testdisk
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: error processing testdisk (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 testdisk
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Now i'm in this state: I cannot purge it since it's not completely installed; and I cannot install it either! :confused:

As a side effect now apt-get (thus synaptic, aptitude,...) are broken because they give error at testdisk which I cannot (un)mark.

I run lucyd linx and keep it constantly up to date.

---

### Post by gandaran on 2011-08-02
did you run 'dpkg --configure -a' with sudo?
and have you tried in synaptic using the fix broken packages option?

---

### Post by esagherardo on 2011-08-02
> **gandaran said:**
> did you run 'dpkg --configure -a' with sudo?
and have you tried in synaptic using the fix broken packages option?

Everything from a root shell. However meanwhile I sorted it out.:D There were several zombi dpkg processes. I tried a clean shutdown, but it was frozen by the check of unattended upgrades, so I had to switch it off by force. After boot, I made a 'dpkg --configure -a' and then 'apt-get install testdisc' ran fine. I then purged and reinstalled testdisk, everything fine.

However I have no idea of what happened.  have a well maintained, constantly updated system. I'll wait a bit for marking the thread as closed, just in case somebody will suggest an explanation.

Thanks a lot anyway.

---

