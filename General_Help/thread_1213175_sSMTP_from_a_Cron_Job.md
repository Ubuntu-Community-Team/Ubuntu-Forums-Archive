---
title: "sSMTP from a Cron Job"
date: 2009-07-14
forum: General Help
---

### Post by cmfarley19 on 2009-07-14
I have a script that backs up my mysql db and wordpress blog.
The script works fine and have worked for a year or more.  I have recently installed sSMTP and added a line to the script to e-mail me a confirmation of a successful back up.  If I run the script manually from the command line, it works just fine.  When it runs as a cron job I receive the following error:
```
/usr/local/scripts/foofarley_backup.sh: line 43: ssmtp: command not found
```

The cron job is part of roots crontab.  I can run the script as root manually and it works fine.

Any thoughts?

Chris

---

