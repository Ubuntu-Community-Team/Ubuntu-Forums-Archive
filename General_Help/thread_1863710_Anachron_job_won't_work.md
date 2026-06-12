---
title: "Anachron job won't work"
date: 2011-10-18
forum: General Help
---

### Post by daniel_sge on 2011-10-18
hi! I wanted to create an anacron job by creating a file at /etc/cron.weekly, but obviously it has never run for 2 weeks.
the file placed at that path has the following attributes:
```
-rwxr-xr-x 1 root root  36 2011-10-01 23:09 rsnapshot
``` 

and the file looks like:

```
#!/bin/sh
/usr/bin/rsnapshot weekly
```

 do you have any solution?

---

### Post by surfer on 2011-10-18
anacron runs the scripts with run-parts. i had some issues because my files were not named correclty. from the run-parts man page:
```
RUN-PARTS(8)                                                               RUN-PARTS(8)

NAME
       run-parts - run scripts or programs in a directory

...

DESCRIPTION
...
       If  neither  the  --lsbsysinit  option  nor the --regex option is given then the
       names must consist entirely of ASCII upper- and lower-case letters,  ASCII  dig&#8208;
       its, ASCII underscores, and ASCII minus-hyphens.
...

```

what is the filename of your anacron job?

oh, sorry, now i see the filename. so that's not the problem...

---

### Post by daniel_sge on 2011-10-18
what I might add, ist that manually running that script as root definitely works as desired.

Is there any way, I can check Anachron is "running"?

---

### Post by daniel_sge on 2011-10-18
Well, that was the thing. Anacron was not installed (every Howto says, that anacron comes onboard). Isn't Anacron used for automatic updates?

---

