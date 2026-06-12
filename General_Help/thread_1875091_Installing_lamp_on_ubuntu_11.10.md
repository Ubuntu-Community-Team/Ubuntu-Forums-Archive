---
title: "Installing lamp on ubuntu 11.10"
date: 2011-11-04
forum: General Help
---

### Post by God's joy on 2011-11-04
[SIZE=4]I tried to install lamp on my laptop using command line, but the error messages i got were these:   1.Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
2.Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

[/SIZE]

---

### Post by mörgæs on 2011-11-04
Hi, welcome to the fora.

Before adding new stuff we should verify that all present packages are in good condition. What happens if you boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

?

---

### Post by Dangertux on 2011-11-04
Make sure software center and update manager are not running also.

---

