---
title: "LANG=en_US.UTF-8 will not change?"
date: 2009-08-04
forum: General Help
---

### Post by Bruce M. on 2009-08-04
**SOLVED!**

How come LANG=en_US.UTF-8 will not change?

After doing:
```
~$ sudo gedit /etc/environment
```
backing up the one liner and changing it to:
> 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
**LANG=en_CA.UTF-8**
LC_CTYPE=en_CA.UTF-8
LC_NUMERIC=en_CA.UTF-8
LC_TIME=en_CA.UTF-8
LC_COLLATE=en_CA.UTF-8
LC_MONETARY=en_CA.UTF-8
LC_MESSAGES=en_CA.UTF-8
LC_PAPER=en_CA.UTF-8
LC_NAME=en_CA.UTF-8
LC_ADDRESS=en_CA.UTF-8
LC_TELEPHONE=en_CA.UTF-8
LC_MEASUREMENT=en_CA.UTF-8
LC_IDENTIFICATION=en_CA.UTF-8
rebooting the system and I see:
> ~$ locale
**LANG=en_US.UTF-8**
LC_CTYPE=en_CA.UTF-8
LC_NUMERIC=en_CA.UTF-8
LC_TIME=en_CA.UTF-8
LC_COLLATE=en_CA.UTF-8
LC_MONETARY=en_CA.UTF-8
LC_MESSAGES=en_CA.UTF-8
LC_PAPER=en_CA.UTF-8
LC_NAME=en_CA.UTF-8
LC_ADDRESS=en_CA.UTF-8
LC_TELEPHONE=en_CA.UTF-8
LC_MEASUREMENT=en_CA.UTF-8
LC_IDENTIFICATION=en_CA.UTF-8
LC_ALL=
~$

Any help appreciated.

Have a nice day.
Bruce

---

### Post by dcstar on 2009-08-05
> **Bruce M. said:**
> How come LANG=en_US.UTF-8 will not change?

After doing:
```
~$ sudo gedit /etc/environment
```
backing up the one liner and changing it to:

rebooting the system and I see:


Any help appreciated.

Have a nice day.
Bruce

/etc/default/locale

---

### Post by Bruce M. on 2009-08-05
> **dcstar said:**
> /etc/default/locale

Yea, that looks like it's the place all right.

Why have it in to places?

Thanks!

Have a nice day.
Bruce

---

