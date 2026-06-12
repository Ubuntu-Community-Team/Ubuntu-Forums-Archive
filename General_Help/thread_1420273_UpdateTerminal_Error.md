---
title: "Update/Terminal Error"
date: 2010-03-02
forum: General Help
---

### Post by rckchlk on 2010-03-02
Hey all I switched to Ubuntu a few months back and now have a problem I can't figure out and would like a little guidance.  When trying to run Terminal or Synaptic I get the following error...

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Using Karmic and have no idea what package it what is causing the problem.

Thanks all.

---

### Post by switch10 on 2010-03-02
Did you try running??
```
sudo dpkg --configure -a
```

---

### Post by rckchlk on 2010-03-03
Ran the command and found the offending app... uninstalled OpenOffice. Rebooted reinstalled OpenOffice using Synaptic and having same problem when using updates...interesting and will look at it tomorrow.  Thanks for letting me know there were actually two "--" in the command.

---

