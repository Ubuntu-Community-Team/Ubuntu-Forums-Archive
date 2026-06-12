---
title: "Disabled GDM - Back on Reboot"
date: 2006-03-30
forum: General Help
---

### Post by darrengreer on 2006-03-30
Hey all,

First time ubuntu user (as a server, replacing Debian).  I searched the forums on how to disable the GDM on startup, and found the Administration->Services option to disable it.  That worked fine, however, upon reboot, the service is enabled again.

How can I permanently disable GDM from starting at boot?

Thanks,

Darren

---

### Post by ispmarin on 2006-03-30
Edit /etc/X11/default-display-manager and comment the line there.

---

### Post by darrengreer on 2006-03-30
Thanks for the tip, but I am receiving the following:


```
root@nod2:~# ls /etc/X11/default-display-manager
ls: /etc/X11/default-display-manager: No such file or directory
root@nod2:~#
```

---

### Post by darrengreer on 2006-03-30
I created an empty /etc/X11/default-display-manager and now all is well.

Thanks!

Darren

---

### Post by ispmarin on 2006-03-30
You are welcome!

---

