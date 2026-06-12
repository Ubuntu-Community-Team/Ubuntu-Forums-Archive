---
title: "rsnapshot won't run from cron"
date: 2009-08-03
forum: General Help
---

### Post by I[AM]SMRT on 2009-08-03
For some reason rsnapshot won't run off my cron, which is annoying because I want to make my backups automatic. Here's my crontab, any ideas? 

```
# m h  dom mon dow   command
0 0 * * * /usr/local/bin/rsnapshot sync && /usr/local/bin/rsnapshot daily
30 23 * * 7 /usr/local/bin/rsnapshot weekly
0 23 1 * * /usr/local/bin/rsnapshot monthly
```

EDIT: Figured out my problem. Since I installed rsnapshot from the repositories, the rsnapshot executable is located in /usr/bin not /usr/local/bin so that my crontab now looks like:

```
# m h  dom mon dow   command
0 0 * * * /usr/bin/rsnapshot sync && /usr/bin/rsnapshot daily
30 23 * * 7 /usr/bin/rsnapshot weekly
0 23 1 * * /usr/bin/rsnapshot monthly
```

---

### Post by acy76 on 2010-01-18
Thank you for this - I was scratching my head as to why the snapshots were not running from the crontab, and I had the same error (no doubt because I was not careful when I copied the crontab entries over from the official man page).

---

