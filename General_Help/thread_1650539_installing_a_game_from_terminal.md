---
title: "installing a game from terminal?"
date: 2010-12-21
forum: General Help
---

### Post by joelkat on 2010-12-21
[http://assault.cubers.net/download.html](http://assault.cubers.net/download.html) at the bottom it says run that command in terminal but in terminal it says E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? what do I do?

---

### Post by WorMzy on 2010-12-21
You must not have included "sudo" in the command. That elevates your account to root level for a short amount of time, allowing you to run things which your user cannot normally run.

---

### Post by joelkat on 2010-12-21
in what part is that
 like whre do I put it

---

### Post by WorMzy on 2010-12-21
```
_sudo_ apt-get install libsdl1.2 libsdl-image1.2 libopenal1 libsdl-ttf2.0-0 
```

---

### Post by madjr on 2010-12-23
you might also grab it here:

[http://www.playdeb.net/updates/Ubuntu/10.10/?category=FPS](http://www.playdeb.net/updates/Ubuntu/10.10/?category=FPS)

read first the instructions for installing software from playdeb

---

