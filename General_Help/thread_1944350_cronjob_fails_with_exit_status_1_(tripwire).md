---
title: "cronjob fails with exit status 1 (tripwire?)"
date: 2012-03-21
forum: General Help
---

### Post by skippercanfly on 2012-03-21
Hi folks,

I have been googling and fighting for a while but I was not able to find a solution :/

I have an error every morning from my daily cronjobs.
(CRON) error (grandchild #12666 failed with exit status 1)

I checked /var/log/syslog and I can see that this error occurs at the time that tripwire cronjob is running.
Furthermore, when I uninstalled tripwire this error did not occur anymore. So, it must be tripwire that causes this error.
However, tripwire cronjob is being executed normally as it is reporting.

Any idea how i can solve this?

Thanks in advance

---

### Post by skippercanfly on 2012-04-18
I found the solution some time but i forgot to update this post
I am updating in case somebody else will have this problem in the future...

I added "|| exit 0" in the end o the daily cronjob (/etc/cron.daily/tripwire) so now it looks like this..


#!/bin/sh -e

tripwire=/usr/sbin/tripwire

[ -x $tripwire ] || exit 0

umask 027

$tripwire --check --quiet --email-report \
|| exit 0

---

### Post by HiImTye on 2012-04-18
thats not really a solution, that's just telling the script to lie about the last status and replace it with status 0

---

### Post by skippercanfly on 2012-04-18
yeah i know,
but the script is running and reporting the only problem is that in the end of the mail it says...

All rights reserved.
run-parts: /etc/cron.daily/tripwire exited with return code 7

do you have the right solution for this?

---

### Post by HiImTye on 2012-04-18
if it has an exit code of 7 then that means that it encountered a run-time error
```
Tripwire exit status can be interpreted by the following mask:
1: run-time error. aborted.
2: files added
4: files deleted
8: files changed
```
4+2+1=7

---

### Post by skippercanfly on 2012-04-18
thnx for your help HiImTye,

so for me to understand better, how can I solve/find what is causing this?

what exactly does it mean that it encounters a run-time error?

---

### Post by Cyclane on 2012-04-18
What happens if you manually run '/usr/sbin/tripwire --check --quiet --email-report'?

---

### Post by skippercanfly on 2012-04-18
from the screen output I can see that the scan is finishing normally without any error.

---

