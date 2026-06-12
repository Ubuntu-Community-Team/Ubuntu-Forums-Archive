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

and yes, I'm looking at firefox serving localhost too. ctrl-r, ctrl-r, ctrl-r... still there.  I'm going nuts here.

---

### Post by ace2005 on 2006-02-04
Was it compiled from source?

Try installing it and then completely removing it in Synaptic

---

### Post by comforteagle on 2006-02-04
[QUOTE=ace2005]Was it compiled from source?

Try installing it and then completely removing it in Synaptic[/QUOTE]

No it wasn't.  Synaptic doesn't see anything "php" installed.

---

