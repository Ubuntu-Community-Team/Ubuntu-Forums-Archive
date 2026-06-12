---
title: "Command not found. Please Help!"
date: 2011-08-02
forum: General Help
---

### Post by MikeBren19 on 2011-08-02
Hi, Im trying to uninstall  Vexira Scandaemon on my Ubuntu 10.10 and Im having a hardtime removing it. it says run the uninstall
script as the root. I tried to go to root and getting an error command not found. The vascand-uninstall.pl script is inside bin folder on home. 

=========================================
mikebren@ubuntu:~$ vascand-uninstall.pl

Vexira Scandaemon Uninstall script
Copyright (c) 2005-2006 Vexira Ltd.

Please run this uninstall script as the root
Uninstallation aborted.
mikebren@ubuntu:~$ sudo -s
root@ubuntu:~# vascand-uninstall.pl
vascand-uninstall.pl: command not found
root@ubuntu:~# 

==========================================

I tried also: 

==========================================

root@ubuntu:/bin# vascand-uninstall.pl
vascand-uninstall.pl: command not found
root@ubuntu:/bin#

==========================================

Any help will be much appreciated. Thanks. noob here..:(

---

### Post by Wim Sturkenboom on 2011-08-02
I don't think that the bin directory in your home directory is in root's path

so as root
```

/home/mikebren/bin/vascand-uninstall.pl

```
should do the trick

or (again as root)
```

cd /home/mikebren/bin
./vascand-uninstall.pl

```

---

### Post by MikeBren19 on 2011-08-02
Will try this and get back to you. Thanks a lot. :)

---

