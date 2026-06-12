---
title: "Indicator-appmenu"
date: 2012-08-19
forum: General Help
---

### Post by mayagrafix on 2012-08-19
I started getting this message when I shutdown:

[B]Problem in indicator-appmenu

The problem cannot be reported: 

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs: 

tzdata[/B]

Indicator-appmenu: what is it and why do I need it...

what should I do? Thanks for any help and sugestions:KS

---

### Post by llamabr on 2012-08-19
try a:

```
sudo apt-get update && apt-get upgrade
```

and then try again.  That should fix it.

---

### Post by mayagrafix on 2012-08-19
Thanks. Lotsa downloaded code, ends with this:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

is this important?

Thanks:KS

---

### Post by raja.genupula on 2012-08-20
are you trying as root ? 

if not then try as root but even trying with root you still getting these problems , open your terminal and type this 

```
sudo rm -rf /var/lib/dpkg/lock
```

then try again.

---

