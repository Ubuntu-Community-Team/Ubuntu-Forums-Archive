---
title: "Booting starts Krusader 11 times"
date: 2010-10-27
forum: General Help
---

### Post by OldAlgis on 2010-10-27
I am using kubuntu 10.10 as my main OS. I've got installed  software for a number of applications as binaries from ubuntu 10.10 repositories.

When I boot the PC, Krusader file manager program is invoked 11 times,  for some mysterious reason. I had a laugh at first, but it is getting monotonous - each boot I have to click x 11 times to close a copy of the Krusader...

BTW, Krusader is my preferred file manager.  

Please suggest actions, including commands on CLI, to track down the problem and to eliminate it.

---

### Post by Ganton on 2010-11-02
The bug can be found in [https://bugs.launchpad.net/ubuntu/+source/krusader/+bug/641650](https://bugs.launchpad.net/ubuntu/+source/krusader/+bug/641650)

---

### Post by OldAlgis on 2010-11-02
> **Ganton said:**
> 
The bug can be found in [https://bugs.launchpad.net/ubuntu/+source/krusader/+bug/641650](https://bugs.launchpad.net/ubuntu/+source/krusader/+bug/641650)

This bug says it all.  I had not realised that this version of Krusader was beta 1... Hopefully it will be fixed soon.  In the meantime a decent work-around is:
```

sudo killall krusader

```
No more multiple copies opened at booting.  So there is just the annoyance of one command entry before logging off!

Thank you Ganton - SOLVED!

---

### Post by Ganton on 2010-12-10
In [https://bugs.kde.org/show_bug.cgi?id=240319](https://bugs.kde.org/show_bug.cgi?id=240319) they said that a workaround was useful to avoid the problem: 

Disable the splash screen (Go to Krusader, to the menu Setting => Startup => Show splashscreen)

---

### Post by Bazilio on 2011-01-03
Thank you, Ganton!
This solution works.

---

