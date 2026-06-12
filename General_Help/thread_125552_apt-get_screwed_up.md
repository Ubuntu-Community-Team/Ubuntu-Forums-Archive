---
title: "apt-get screwed up?"
date: 2006-02-04
forum: General Help
---

### Post by comforteagle on 2006-02-04
can someone explain this?:


steve@ubuntu:~/bin$ sudo apt-get remove apache2
Reading package lists... Done
Building dependency tree... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
steve@ubuntu:~/bin$ sudo /etc/init.d/apache2 restart
 * Forcing reload of web server  (Apache2)...                                                  [ ok ]
steve@ubuntu:~/bin$

---

### Post by dcstar on 2006-02-04
[QUOTE=comforteagle]can someone explain this?:


steve@ubuntu:~/bin$ sudo apt-get remove apache2
Reading package lists... Done
Building dependency tree... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
steve@ubuntu:~/bin$ sudo /etc/init.d/apache2 restart
 * Forcing reload of web server  (Apache2)...                                                  [ ok ]
steve@ubuntu:~/bin$[/QUOTE]
Yes, the software was not installed using the apt system, it may have been installed using another method.

---

