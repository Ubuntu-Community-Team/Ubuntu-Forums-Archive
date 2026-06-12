---
title: "Cron query"
date: 2010-09-22
forum: General Help
---

### Post by Zenmij on 2010-09-22
Hi guys, just wanted to ascertain something here:

Looking through /var/log/auth.log I noticed:

```
Sep 19 17:17:01 xxxx-xxxx CRON[6426]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 19 17:17:02 xxxx-xxxx CRON[6426]: pam_unix(cron:session): session closed for user root

```

As I don't have a cron job running, I looked through crontab, and notice:

```
root cd / && run-parts --report /etc/cron.hourly
```

but I have no cronjob set hourly, so this is a waste of time right? checking hourly for something thats never going to be there?

---

