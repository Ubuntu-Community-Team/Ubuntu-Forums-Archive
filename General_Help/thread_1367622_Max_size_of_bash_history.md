---
title: "Max size of bash history?"
date: 2009-12-29
forum: General Help
---

### Post by growthmetal on 2009-12-29
I set $HISTSIZE and $HISTFILESIZE both to 50 trillion and my bash history stopped working.  Anyone have any idea why?

---

### Post by upbeat.linux on 2009-12-30
I'm guessing there is a buffer overflow error somewhere. 

HISTSIZE is somewhat different from HISTFILESIZE. A good explanation can be found here:

[http://www.linux.com/archive/feature/114148](http://www.linux.com/archive/feature/114148)

What are you trying to achieve?  If you just want an archive of all past commands you might want to follow up reading these articles:

[http://www.bash-hackers.org/wiki/doku.php/mirroring/bashfaq/088](http://www.bash-hackers.org/wiki/doku.php/mirroring/bashfaq/088)

[http://www.debian-administration.org/articles/543](http://www.debian-administration.org/articles/543)

---

