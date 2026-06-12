---
title: "Apropos doesn't work"
date: 2010-02-02
forum: General Help
---

### Post by Moose32315 on 2010-02-02
As the title says the command apropos doesn't seem to work.  By that I mean that whatever I try to find apropos always returns nothing appropriate.  I've tried using the makewhatis command to create the database, but that command doesn't exist on my system.  I've also tried updating man with mandb, and that hasn't helped either.  I'm unsure what to try now.

---

### Post by bluefrog on 2010-02-02
apropos who

returns what on your system?

---

### Post by gmargo on 2010-02-02
You should give some info on what OS version you're running.  The man-db package supplies apropos and man as well as the cron scripts to update the index.

Some things you can check:

[LIST]
[*]/etc/manpath.config (maybe this got wiped out?)
[*]apropos -d (-d is debug option)
[*]/var/cache/man/ (there should be an recent index.db file)
[/LIST]

---

### Post by Moose32315 on 2010-02-02
I don't know what happened but when I typed apropos who it actually worked.  The results are below. I tried a few things, but they sounded like they didn't do anything.  It seems to be working now though.  Thanks

ubuntu@ubuntu:~$ apropos who
at.allow (5)         - determine who can submit jobs via at or batch
at.deny (5)          - determine who can submit jobs via at or batch
from (1)             - print names of those who have sent mail
w (1)                - Show who is logged on and what they are doing.
w.procps (1)         - Show who is logged on and what they are doing.
who (1)              - show who is logged on
whoami (1)           - print effective userid
whois (1)            - client for the whois directory service

---

