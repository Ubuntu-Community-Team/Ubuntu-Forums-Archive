---
title: "help me to run xdmx"
date: 2011-08-13
forum: General Help
---

### Post by loolooyyyy on 2011-08-13
i've read thousand of articles, followed millions of links but i couldn't get it working,
can some one simply explains to me what should i do?

i connect laptop-slave to laptop-master via cable on eth0
i give them both manually an address, slave:192.168.0.77 , master:192.168.0.7
i then stop X server by "sudo stop gdm" on both laptops WHICH if i dont it says x is already running=>error
from slave i ssh to master
from ssh command prompt on slave i run
"sudo startx --/usr/bin/Xdmx :1 +xinerama -display 0.0 -display localhost:0.0 -norender -noglxproxy
but it doesnt work, it gives error

---

### Post by loolooyyyy on 2011-08-13
the error is
(EE) Failed to load module "fglrx" (module does not exist, 0)

---

### Post by headvampyre@hotmail.co.uk on 2012-02-05
Hi, don't really want to bring up an old thread, but I'd say that's because one of the machines doesn't have the AMD/ATi drivers for the graphics card

---

### Post by loolooyyyy on 2012-02-13
oh tanx it's still interesting for me,
one of them has an intel card, so, if i install it, though it's not needed by the machine itself, will it work?
(the other one ati)

---

