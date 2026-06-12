---
title: "gksudo shutdown -hP help"
date: 2006-03-01
forum: General Help
---

### Post by Herd on 2006-03-01
Im trying to make a launcher to "gksudo shutdown -hP +45".  The problem is that the flags that I want to modify 'shutdown' are in fact modifying 'gksudo' and I end up with gksudo running its help command.  It works fine when just using sudo in the terminal however I would like to do it with gksudo.  Anybody know how to do this?  Thanks a lot.

---

### Post by dcstar on 2006-03-01
[QUOTE=Herd]Im trying to make a launcher to "gksudo shutdown -hP +45".  The problem is that the flags that I want to modify 'shutdown' are in fact modifying 'gksudo' and I end up with gksudo running its help command.  It works fine when just using sudo in the terminal however I would like to do it with gksudo.  Anybody know how to do this?  Thanks a lot.[/QUOTE]
"gksudo" is specifically to run X applications, do not use it to run command line apps or scripts - use sudo.

---

