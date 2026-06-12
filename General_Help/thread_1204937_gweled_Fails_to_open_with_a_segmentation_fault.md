---
title: "gweled Fails to open with a segmentation fault"
date: 2009-07-05
forum: General Help
---

### Post by beastrace91 on 2009-07-05
I just installed gweled on my netbook (running Jaunty 9.04 32bit) and I get the following message when trying to load it:

```
jeff@eeetop:~$ gweled
Could not initialize sound, reason: Could not open sound device
Segmentation fault
```

Any ideas how I can make this work?

~Jeff

---

### Post by Scifly on 2009-07-27
This bug has been reported in Launchpad and I have the same problem.  I found that if you try to start gweled from the command line immediately after it seg faults it starts OK.

---

