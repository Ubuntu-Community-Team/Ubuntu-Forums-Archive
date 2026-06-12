---
title: "CRON format help"
date: 2010-10-09
forum: General Help
---

### Post by sr_guy on 2010-10-09
I am setting up a cron job on my DD-WRT router to execute a WOL command, and would like to know if what I have is correct.

Format:

Execute @ 12:00 on Wed, Thur, Fri, Sat every month/Yr

0 12 * * 2345 root /usr/sbin/wol -i 192.168.1.255 00:00:00:00:00:00

---

### Post by t4thfavor on 2010-10-09
I always like this one:

[http://adminschoice.com/crontab-quick-reference](http://adminschoice.com/crontab-quick-reference)

All looks well, I was wrong about 2345
```
*     *     *   *    *        command to be executed
-     -     -   -    -
|     |     |   |    |
|     |     |   |    +----- day of week (0 - 6) (Sunday=0)
|     |     |   +------- month (1 - 12)
|     |     +--------- day of        month (1 - 31)
|     +----------- hour (0 - 23)
+------------- min (0 - 59)

```

---

### Post by sr_guy on 2010-10-09
Wed-Sat @ 12

is this right?

0 12 * * 3456 root /usr/sbin/wol -i 192.168.1.255

---

### Post by t4thfavor on 2010-10-09
The article says it all, but it should be 3-6...

---

