---
title: "Problems dpkg"
date: 2006-03-01
forum: General Help
---

### Post by sharif_aly on 2006-03-01
i have this proplem :
[B]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.[/B]

I Run this command

**sudo dpkg --configure -a**
[B]
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
Aborted[/B]

---

### Post by joshuapurcell on 2006-03-05
Looks like this is a known bug that is fixed by using --forcedepends when giving the dpkg command. I haven't tried this, but I found this link:
[http://lists.debian.org/debian-devel/1999/05/msg02534.html](http://lists.debian.org/debian-devel/1999/05/msg02534.html)

---

### Post by sharif_aly on 2006-03-06
i can't remove this package .. gforge-db-postgresql

don't know why ?

---

