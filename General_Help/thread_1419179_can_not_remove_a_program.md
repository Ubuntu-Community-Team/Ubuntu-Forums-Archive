---
title: "can not remove a program"
date: 2010-03-01
forum: General Help
---

### Post by drdob on 2010-03-01
i tried to install Stellarium and it crashed the lot. i tried to uninstalling it but it refused to uninstall . i tried in synaptic manager no go, i tried in terminal and that was to no go. i have tried to reinstall but again it would not install, and would not uninstall, now what do i do??
any ideas yours Dr Dob

---

### Post by MelDJ on 2010-03-01
what error comes up when you uninstall?

---

### Post by namluc on 2010-03-01
sudo aptitude remove stellarium should remove all horrors.

---

### Post by namluc on 2010-03-01
you might need to kill it first if it is still running, find the programe that monitors cpu cycles and what not, look at the processes, disable and kill the relevant process if you see it running

---

### Post by garolou on 2010-03-01
from a terminal, try the following to make sure everything is properly removed:
```
sudo apt-get purge stellarium
sudo apt-get autoremove stellarium
```

from man:
> 
purge
purge is identical to remove except that packages are removed and purged (any configuration files are deleted too).

autoremove
autoremove is used to remove packages that were automatically installed to satisfy dependencies for some package and that are no more needed.


---

### Post by drdob on 2010-03-02
i get this "Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing: "  i tried the other way that have been suggested, with no success. DrDob

---

### Post by wojox on 2010-03-02
Try this:

```
sudo dpkg --remove --force-remove-reinstreq stellarium
```

---

### Post by drdob on 2010-03-04
thank you all for your help but none of it worked, so i have decide to upgrade to 9.10
thank you for your help DrDob

---

