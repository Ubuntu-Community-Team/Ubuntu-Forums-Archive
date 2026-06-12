---
title: "How to limit the size of /var/log/messages?"
date: 2009-07-16
forum: General Help
---

### Post by neilengineer on 2009-07-16
I want to limit the size of /var/log/messages.

After searching the Net, logrotate is one solution. But it seems difficult to config.

Any other easier tool to limit /var/log/messages?

:confused:

---

### Post by sedawk on 2009-07-16
On my Ubuntu desktop logrotate seems to be running by default, although
I cannot figure out why (no cronjobs!). So the default installation
seems to bring a proper configuration. Simply add a cronjob if you
do not reboot your machine on a regular basis.

```

$ ls -1 /var/log/mess*
/var/log/messages
/var/log/messages.0
/var/log/messages.1.gz
/var/log/messages.2.gz
/var/log/messages.3.gz

```

---

### Post by neilengineer on 2009-07-16
Thank you for replying. I will look into it.

Maybe I turned some service off. I'll check.

---

