---
title: "Two Errors with Package Manger and not sure where to start"
date: 2009-08-11
forum: General Help
---

### Post by hufferd on 2009-08-11
Hi there I am getting two errors with the package manager one when trying to install Virtual box 3.0 and also when trying to run Synaptic ?? 

I have no idea where to go to try and fix this I have enclosed screen shots 

any ideas thanks

Oh and just to mention I have tried rebooting that does not help either

---

### Post by michy99 on 2009-08-11
For the first one, make sure that no other package management program is open.

For the second, run this command in a terminal:```
sudo dpkg --configure -a
```

---

