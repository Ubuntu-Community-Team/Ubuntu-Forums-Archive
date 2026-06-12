---
title: "unison run from cron fails"
date: 2010-08-26
forum: General Help
---

### Post by ultim8 on 2010-08-26
Hey all,

I have unison set up (using the .unison/default.prf config file) to sync certain directories on my work computer with my home computer.

If I run unison from the commandline it works as expected:
```
unison -batch -silent
```
I set it up to run as a crontab under my user to run each night at 1AM:
```
# m h  dom mon dow   command
  0 1  *   *   *     /usr/bin/unison -batch -silent
```
...but it seems to fail each night... as shown from .unison/unison.log:
```
Fatal error: Lost connection with the server
Fatal error: Lost connection with the server
Fatal error: Lost connection with the server
```
Each "Fatal error..." line corrasponds to each night that cron attempted to run unison.

Anyone have an idea what is going on here?

---

### Post by DaithiF on 2010-08-26
Hi, try redirecting output to a log file:
```
  0 1  *   *   *     /usr/bin/unison -batch -silent > /home/you/unisoncron.log 2>&1
```

---

### Post by ultim8 on 2010-08-26
Good idea... I just did that and saw ssh permission errors.  I had a passpharse set up for my public key... and cron doesn't access my keyring so it was failing on connect.  Thanks for you help.

---

