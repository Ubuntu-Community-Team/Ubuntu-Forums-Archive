---
title: "SVN error on gnome-terminal startup"
date: 2010-05-27
forum: General Help
---

### Post by altonbr on 2010-05-27
I've been using SVN for a little while and I'm not sure what I did but now every time I open a terminal, this error pops up:
```
svn: warning: '.' is not a working copy
```
I read my ~/.bashrc and saw nothing SVN related.

---

### Post by geirha on 2010-05-27
Your .bashrc could be running/sourcing another script that does do something svn related.

---

### Post by altonbr on 2010-05-27
> **geirha said:**
> Your .bashrc could be running/sourcing another script that does do something svn related.
Turns out it was [RabbitVCS]("http://rabbitvcs.org/") (a TortoiseSVN clone) or some svn dependency it installed. Luckily my work just switched to git so I uninstalled it and the error went away.

---

### Post by ibuclaw on 2010-05-27
Or /etc/bash.bashrc could be.

ie: the /etc/bash_completion.d directory.

---

