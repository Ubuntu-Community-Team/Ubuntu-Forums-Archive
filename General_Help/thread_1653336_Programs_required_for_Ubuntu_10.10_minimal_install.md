---
title: "Programs required for Ubuntu 10.10 minimal install"
date: 2010-12-26
forum: General Help
---

### Post by dmillerw on 2010-12-26
The full version of Ubuntu 10.10 has been having issues with my computer, so I'm going to attempt a minimal install.

What programs are required to achieve this, including indicator applets and the like.

---

### Post by dmillerw on 2010-12-26
Anyone know?

---

### Post by rascal+1/2 on 2011-01-02
[http://ubuntuforums.org/showthread.php?t=997571&highlight=minimal+install](http://ubuntuforums.org/showthread.php?t=997571&highlight=minimal+install)

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by 1clue on 2011-01-02
The term "minimum install" means different things to different people.

I would get the bare server (non-X) installation going, then add xorg, then add the end-user apps you want to use.  Then fill in the applets later.  You will want to install xorg by name, because otherwise if you uninstall the things depending on it you may uninstall X if you run system cleanup type tasks.  Maybe use that thread you got a link to for reference in case you're missing something you don't have an answer for.

---

