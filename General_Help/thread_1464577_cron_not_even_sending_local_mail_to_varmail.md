---
title: "cron not even sending local mail to /var/mail/"
date: 2010-04-28
forum: General Help
---

### Post by yang on 2010-04-28
I'm using a very plain Ubuntu Server 9.04, and cron isn't delivering any mail to my /var/mail/USER (the file hasn't even been created). Here's my full crontab:
```

# m h  dom mon dow   command
 15 *  *   *   *     $HOME/.cron/sync-bookmarks.bash

```
If I add
```

# m h  dom mon dow   command
 15 *  *   *   *     $HOME/.cron/sync-bookmarks.bash >& /tmp/log

```
then I see the stdout and stderr in /tmp/log. I'm not (yet) interested in actual remote email delivery, just local delivery to the mail spool file. Why isn't mail working? Thanks in advance for any tips.

---

