---
title: "Synaptic Package Manager Issue"
date: 2011-05-19
forum: General Help
---

### Post by tyrick on 2011-05-19
Helllo!

I was trying to install wine with synaptic package manager, and mid installation my pc crashed... >.< (Might have been a bad omen)

Now, when I try to go to the package manager, I get a screen that says an error occurred and,

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


TT.TT   Any ideas!?

Thanks,
Tyrick

---

### Post by r-senior on 2011-05-19
Open up a terminal window and enter:

```
sudo dpkg --configure -a
```

Once it's done it's thing, try Synaptic again.

---

### Post by Rubi1200 on 2011-05-19
You might want to also run ```
sudo apt-get update
``` as well.

If the command posted by r-senior returns any errors, please post the exact information here so we can troubleshoot what is going on.

Thanks.

---

