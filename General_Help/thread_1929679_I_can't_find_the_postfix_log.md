---
title: "I can't find the postfix log"
date: 2012-02-22
forum: General Help
---

### Post by Nailox on 2012-02-22
Hi all. Im using ubuntu 10.4 LAMP on a VPS. I need to find the postfix or the mail log but I can't ! I tried:
/var/log - nothing related to mail 
used find and locate to search for mail.log - nothing

So anyone experienced with postfix can tell me where is the log?

---

### Post by dcstar on 2012-02-23
> **Nailox said:**
> Hi all. Im using ubuntu 10.4 LAMP on a VPS. I need to find the postfix or the mail log but I can't ! I tried:
/var/log - nothing related to mail 
used find and locate to search for mail.log - nothing

So anyone experienced with postfix can tell me where is the log?

```
/var/log/mail.err
/var/log/mail.info
/var/log/mail.log
/var/log/mail.warn
```

are all on my system.

You should also probably have a /etc/rsyslog.d/postfix.conf file as well.

---

