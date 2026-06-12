---
title: "Eclipse error, ubuntu 11.10"
date: 2011-10-14
forum: General Help
---

### Post by elion on 2011-10-14
after upgrade to oneiric Eclipse start fails, with error:
```
plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.200.v20090520: cannot open shared object file: No such file or directory
```
While writing this thread found solution. Problem in the ini file: /usr/lib/eclipse/eclipse.ini 

fix:
```
sudo mv /usr/lib/eclipse/eclipse.ini /usr/lib/eclipse/eclipse.ini.bup
```

---

### Post by evredenb on 2011-11-13
Had the same problem, solution worked for me.

---

### Post by cellurl on 2012-08-16
had same problem, worked for me.

---

