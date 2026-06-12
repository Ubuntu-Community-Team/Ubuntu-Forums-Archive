---
title: "ls -l: timestamp format: shell vs cron"
date: 2010-06-16
forum: General Help
---

### Post by NewKindaArt on 2010-06-16
Setup: 10.04 server with "bash" as /bin/sh

When I run "ls -l" in a shell I get the following format:

```
-rw-r----- 1 syslog adm 0 2010-06-13 06:53 /var/log/user.log
```

Whereas if "ls -l" executes from a cron job the format is:

```
-rw-r----- 1 syslog adm 0 Jun 13 06:53 /var/log/user.log
```

Notice the different time format.  Now I could fix this by changing the cron job to

```
ls -l --time-style=+%Y-%m-%d\ %H:%M ...
```

but I'm interested in knowing why this behavior occurs.  What's different between the cron job and the shell?  Thanks!

---

### Post by arrange on 2010-06-16
I think *cron* runs under different environment from the user. It means it uses for example different locale. You can compare locales by running ```
locale
``` from a console and from *cron*.

---

