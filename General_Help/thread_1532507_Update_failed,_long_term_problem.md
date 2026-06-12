---
title: "Update failed, long term problem"
date: 2010-07-16
forum: General Help
---

### Post by LanceyD on 2010-07-16
I haven't been able to update for months because of this problem.  I cannot figure out what this broken pipe is and I have tried to fix it through the Package Manager a couple of times.  

Even though it says update complete i've had the same 108 updates "ready to install" for months.

Ubuntu 9.10
[IMG]http://www.koedjoinery.com/pictures/Screenshot-6.jpg[/IMG]

[IMG]http://www.koedjoinery.com/pctures/Screenshot-6.jpg[/IMG]

---

### Post by gmargo on 2010-07-16
Why don't you try the obvious?  Make a backup of the /var/lib/dpkg/status file, then edit the file, go to line 5951 and remove the offending character(s).  After that you may be better off running "aptitude update" and "aptitude full-upgrade" from the command line.  Easier to see errors than with the graphical client.

---

### Post by LanceyD on 2010-07-16
It takes someone else to point out the obvious sometimes, problem sorted!  Thanks :D

---

