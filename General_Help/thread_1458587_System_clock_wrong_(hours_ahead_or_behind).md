---
title: "System clock wrong (hours ahead or behind)"
date: 2010-04-20
forum: General Help
---

### Post by greenbreen on 2010-04-20
I've been having this problem for quite some time now, and I finally decided to tackle it.  It took me several hours of research to figure it out, so I wanted to post my findings in case anyone else has this problem.  For my particular problem, it turned out that I had a line in my .profile file in my home folder that was setting the timezone, but I had moved to a different timezone.  The offending line was
```
TZ='America/Los_Angeles'; export TZ
```
To fix it, I first had to set my BIOS time correctly.  To do this, I rebooted my computer and pressed F2 (it may be DEL, F10, ESC, or something else on your computer) when my computer flashed "Press F2 to enter setup" as soon as it started up.  I changed the time in BIOS, save the change (on my computer with F10), and then booted to Ubuntu.  Then I executed
```
sudo gedit .profile
```
from a terminal and added a # before the offending line.  Then I rebooted, and my system time was correct.

If that doesn't fix it, it's possible your TZ variable is being set by something else. Check the TZ variable by issuing
[HTML]echo $TZ[/HTML]
in a terminal.  If the timezone is correct, your problem has a different cause than mine.

Here is a link to another post regarding the same problem, but with a different cause:
[[COLOR="Blue"]_ubuntuforums.org/showthread.php?t=633848_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=633848")

I hope this  helps!

---

