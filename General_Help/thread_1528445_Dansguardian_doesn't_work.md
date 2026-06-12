---
title: "Dansguardian doesn't work ?"
date: 2010-07-10
forum: General Help
---

### Post by gabo.cr on 2010-07-10
I am trying to configure Dansguardian following [this instructions]("https://help.ubuntu.com/community/DansGuardian").

However, Dansguardian is not blocking sites and I am getting this errors when I run this commands:

```
$ dansguardian
Unable to setgid()

```

> $ sudo /etc/init.d/dansguardian start
 * Starting DansGuardian dansguardian                                                             Error opening/creating log file. (check ownership and access rights).
I am running as dansguardian and I am trying to open /var/log/dansguardian//access.log
                                                                                           [fail]

So I checked the ownership for that folder and it is the way is supposed to be:

> $ ls -l /var/log/dansguardian/
total 4
-rw-r--r-- 1 proxy proxy 423 2010-07-10 16:43 access.log

I added myself to the "proxy" group, just to see if that would help, but it didn't.

I know Dansguardian can be a pain to configure, but I feel that I'm pretty closed to get it done.
Any ideas ?
[-o<

---

