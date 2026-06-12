---
title: "fter a shutdown the computer won't power down"
date: 2010-05-16
forum: General Help
---

### Post by doddo on 2010-05-16
Hello! just recently I upgraded from 9.10 to 10.04. Now whenever I shut down computer gets stuck after umounting disks etc, so I have to shut down using power button, similar to this error:

[http://ubuntuforums.org/archive/index.php/t-486848.html](http://ubuntuforums.org/archive/index.php/t-486848.html)

Anyone know how to fix this?

:confused::confused::confused:

---

### Post by Bill magee on 2010-05-16
Did you try the fix suggested by Atari130xe in the link you supply?

edit /etc/modules

add apm power_off=1

Just curious. I have no idea if it would work for your problem.

---

### Post by doddo on 2010-05-16
Hello!

Don't think I've got no apm module :confused::confused::confused:

```
[doddo@g0rion ~]$ modinfo apm
ERROR: modinfo: could not find module apm

```

---

