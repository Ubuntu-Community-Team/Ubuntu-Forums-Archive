---
title: "VLC opens when Volumes are Mounted"
date: 2010-12-15
forum: General Help
---

### Post by robwgibbons on 2010-12-15
For some reason, whenever I mount a volume, VLC Media Player tries to open it as if it is the default program.

I'm not sure what created the problem, but I wonder if anyone has seen it before or has a solution.

I'm running a recent and up-to-date version of 64-bit Ubuntu 10.10.

---

### Post by mc4man on 2010-12-15
Not sure if this is a variation of a fairly common occurrence - could run run this and post the result. This line, if there, is the one of interest
inode/directory=

```
cat ~/.local/share/applications/mimeapps.list
```

---

### Post by robwgibbons on 2010-12-15
mc4man, I can't thank you enough.

I opened up "~/.local/share/applications/mimeapps.list" in gedit and removed the line "inode/directory=". Totally fixed the problem. 

Thanks a ton.!

---

### Post by mc4man on 2010-12-15
In the future - when using the r. click menu - 'open with' - 'other application' you must uncheck the 'Remember this application ...' or the default will be changed. 
The option should never be enabled when doing on folders, for files it will also change the default, though that isn't quite the problem as on folders.

(finally got a semi-fix thru to have that option disabled by default - unfortunately the 'fix released' will only be applied atm to nautilus in natty.

---

