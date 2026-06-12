---
title: "Damaeon rights"
date: 2009-12-16
forum: General Help
---

### Post by StarThorn1 on 2009-12-16
How can I tell if a daemon has rights to a certan file?

---

### Post by eric3_14159 on 2010-01-15
It depends on what you mean by "daemon", whether it's a session startup program, a /etc/init.d script, a cron job, or something else entirely.

In any case, though, it will have a user ID, and so will use whatever permissions that user normally has.

If you know the name of the daemon, and it's running, you can run the command
```
ps aux | grep daemonname
```
And you'll see some output about the process including, in the first column, the username.

---

