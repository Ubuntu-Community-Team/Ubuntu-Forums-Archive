---
title: "unable to remove ubuntu tweak"
date: 2009-11-04
forum: General Help
---

### Post by halligan46 on 2009-11-04
I attempted to install ubuntu tweak using synaptic pkg mgr in jaunty I'm unable to remove so synaptic doesn't work at all. any advice would be appreciated, I've tried the manuals but to no avail. Thanks in advance JIM

---

### Post by lidex on 2009-11-04
Run this command in a terminal:
```
sudo dpkg --configure -a 
```

You can open a terminal from accessories menu.

---

