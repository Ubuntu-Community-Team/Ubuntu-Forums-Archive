---
title: "lshw security bug?"
date: 2009-11-25
forum: General Help
---

### Post by MichaelBurns on 2009-11-25
I just ran lshw as a reguler desktop user (who doesn't have admin priveledges).  I did not even put sudo in front.  It gave me plenty of output regarding my hardware, and the bit that I did understand appears to be correct.  This would not worry me, except in the error stream (stream 2) I got
```
"WARNING: you should run this program as super-user.
```
Now, why in the world would it say something like that to a desktop user and then just run anyway?

Another even more peculiar thing was that the prompt line was momentarily replaced by:
```
CPUID
```
and then, for a slightly longer moment by
```
PCI (sysfs)
```
before going on to display the hardware info output (in stream 1).

Do I need to worry about this (and try to fix it)?

---

### Post by Sam on 2009-11-25
lshw cannot retrieve all the informations if you run as unprivileged user (hence the warning).

The CPUID, PCI (sysfs) stuff is just the name of the current hardware being probed.


Nothing special to worry about! ;)

---

### Post by MichaelBurns on 2009-11-25
Thanks, Sam.  So prompt.

---

### Post by Sam on 2009-11-25
Glad to help you ;)

---

