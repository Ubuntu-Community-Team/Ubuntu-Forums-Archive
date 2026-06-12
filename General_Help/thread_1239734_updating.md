---
title: "updating"
date: 2009-08-13
forum: General Help
---

### Post by newbemac on 2009-08-13
when I attempt to use update manager and install added updates I get this message and no update occures

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what does this mean
newbemac

---

### Post by BslBryan on 2009-08-13
Simply navigate to Applications --> Accessories --> Terminal and copy/paste this in: 
```
sudo dpkg --configure -a
```

---

### Post by BslBryan on 2009-08-13
Ah, I see you're using Xubuntu.  In that case, do the same thing, but you'll have to get to the terminal in a different way.

Sorry my knowledge of Xfce isn't very broad. :P

---

### Post by newbemac on 2009-08-13
that was it.. how easy  thanks

---

