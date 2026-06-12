---
title: "apt/dpkg database backup!?"
date: 2006-02-01
forum: General Help
---

### Post by vyruss on 2006-02-01
I did something really, really stupid (which I won't go into right now) which rendered my Breezy system totally inoperable. Now it's up and running perfectly again, as all my files/configurations were spared but I have this problem:

The apt/dpkg database does not know which packages are installed. The system works fine, as all files are in their right place, but the apt/dpkg system only thinks the basic Breezy packages are installed and not the tons of stuff I've installed from the repositories myself over the past few months.

Is there any chance of there being a backed-up apt/dpkg database somewhere on my system that would rectify this? (e.g. in /var/cache) ?

Many thanks!

---

### Post by lamego on 2006-02-01
How did you get it back working ? Reinstalled it ? If yes than you have overwritten the  packages db, you should reinstall the packages with APT or manually with dpkg -i using the files you may have on  /var/cache/apt/ .

---

### Post by vyruss on 2006-02-02
[QUOTE=lamego]How did you get it back working ? Reinstalled it ? If yes than you have overwritten the  packages db, you should reinstall the packages with APT or manually with dpkg -i using the files you may have on  /var/cache/apt/ .[/QUOTE]

That's exactly what I want to avoid doing :(

If I knew, however, that there is an old version of the package db somewhere on my hard disk, my life would be so much easier...

---

### Post by lamego on 2006-02-02
Even if there was a db backup it would be very wize to replace the current db, if you have reinstalled the system it is very likely that you don't have the exact same package files/version you had before losing the system, you could just break your entire system (again).
If you do intend to playing with system on a way that may break it again make sure you do the backups first...

---

