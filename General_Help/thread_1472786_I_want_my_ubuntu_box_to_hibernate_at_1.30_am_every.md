---
title: "I want my ubuntu box to hibernate at 1.30 am everyday"
date: 2010-05-04
forum: General Help
---

### Post by supermarchino on 2010-05-04
```

costy@costy-desktop:~$ sudo crontab -l
[sudo] password for costy: 
# m h  dom mon dow   command
 30 1   *   *   *    pm-hibernate
costy@costy-desktop:~$

```

There it is. But at 1.30 nothing happens. :(

No need to say that

```

$sudo pm-hibernate

```

does its job flawlessly.

Any help appreciated.

Thanx. Ciao.

---

### Post by Bonster on 2010-05-04
cron is pretty stupid so what you usually do is put the absolute path for the app that your using

so instead of just "pm-hibernate"
you might want to try the absolute location is at:

> /usr/sbin/pm-hibernate

---

