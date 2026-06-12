---
title: "lts-backport-maveric update issue"
date: 2011-08-09
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-08-09
a kernel update showed up today but it will not update the linux headers
[IMG]http://i53.tinypic.com/n1v534.png[/IMG]
[IMG]http://i51.tinypic.com/6fd2mg.png[/IMG]
[IMG]http://i54.tinypic.com/x1zwd5.png[/IMG]
what should i do?
the reason i am using maveric's kernel is for trim support

EDIT:
the package is now present with a newer version

---

### Post by Bart92 on 2011-08-09
Try 

[U][I]sudo apt-get update 

sudo apt-get dist-upgrade

Or

aptitude install -t squeeze - backports maverick
[/I][/U]

---

### Post by pqwoerituytrueiwoq on 2011-08-09
i think i found the issue
the package *linux-headers-2.6.35-30* does not exist maybe it is still being compiled or something

---

### Post by pqwoerituytrueiwoq on 2011-08-11
anyone know where i can report that the package is missing?
deb [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) lucid main

---

### Post by pqwoerituytrueiwoq on 2011-08-15
> **pqwoerituytrueiwoq said:**
> anyone know where i can report that the package is missing?
deb [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) lucid main
anyone able to find the ppa's main page on launchpad?

---

