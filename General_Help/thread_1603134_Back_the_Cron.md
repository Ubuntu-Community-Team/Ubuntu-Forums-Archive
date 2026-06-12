---
title: "Back the Cron"
date: 2010-10-22
forum: General Help
---

### Post by CrusaderAD on 2010-10-22
How can I backup the cron file I have built to manage automated tasks?

---

### Post by DaithiF on 2010-10-22
Hi, you could do it a couple of ways:
1. crontab -l outputs the contents of your crontab to stdout, redirect to a file to capture it, e.g.:
```
crontab -l > /path/to/backup/mycronbackup

```

2. the file containing your crontab will be stored in:
```
/var/spool/cron/crontabs/<username>

```
you could copy the file from there to your backup location.
you'll need sudo privileges to do this though, unlike method 1.

---

### Post by CrusaderAD on 2010-10-25
Excellent, works great!

---

