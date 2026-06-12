---
title: "suspend/hibernate commands freeze ubuntu?"
date: 2010-07-04
forum: General Help
---

### Post by princeofnam on 2010-07-04
out of no where it seems ubuntu no longer wants to cooperate when suspending/hibernating.  the screen will just turn to a black screen without shutting down. each time i have to maually power down my laptop. any ideas?

---

### Post by princeofnam on 2010-07-04
anyone?

---

### Post by backbonee on 2012-03-09
> **princeofnam said:**
> anyone?

Have the same behaviour on P52Jc (Gentoo) with nVidia Optimus.
Solved by adding
```
OnSuspend 10 /usr/bin/eselect rc stop laptop_mode
OnResume 90 /usr/bin/eselect rc start laptop_mode
```to /etc/hibernate/common.conf.

Perhaps it would be helpful for somebody...

---

### Post by ceciliasp on 2012-09-10
Hi Backbonee, I have the same problem with my Lenovo G550 but I don't have the file under etc/hibernete/common.conf.
Actually there is no Hibernate directory at all... shoul I just create the file o should I do something else?
Thanks for the help

---

### Post by ceciliasp on 2012-09-10
Or any other hint would be appreciated!

---

### Post by jaithehulk on 2012-09-11
This might help you guys.
[http://ubuntuforums.org/showthread.php?t=1960220]("http://ubuntuforums.org/showthread.php?t=1960220")

---

