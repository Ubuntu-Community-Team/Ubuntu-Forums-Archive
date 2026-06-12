---
title: "dovecot server not starting correctly on boot; ok after manual kill / reload"
date: 2009-12-30
forum: General Help
---

### Post by intangodelta on 2009-12-30
Hi

This concerns the Ubuntu community maintained configuration of dovecot, installed from the repositories on Ubuntu 9.10.

When Ubuntu starts, it loads dovecot but I can't seem to connect to the server. If I kill the dovecot processes using *sudo killall dovecot* and restart using *sudo dovecot*, everything is fine.

Somehow the startup isn't working but the application is fine - is there anything I can check to find out what's going on?

Thanks

---

### Post by Johnny B on 2009-12-30
check the logs for startup errors:
[http://wiki.dovecot.org/Logging]("http://wiki.dovecot.org/Logging")

---

### Post by intangodelta on 2009-12-30
> **Johnny B said:**
> check the logs for startup errors:
[http://wiki.dovecot.org/Logging]("http://wiki.dovecot.org/Logging")
Done all that - no errors logged, except the one where I killed the processes:

```
paul@gorky:/var/log$ cat mail.info
Dec 29 12:17:27 gorky postfix/master[1692]: daemon started -- version 2.6.5, configuration /etc/postfix
Dec 29 12:17:30 gorky dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Dec 29 12:18:28 gorky postfix/master[1692]: reload -- version 2.6.5, configuration /etc/postfix
Dec 29 21:26:38 gorky dovecot: imap-login: Login: user=<paul>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Dec 29 21:27:58 gorky dovecot: Killed with signal 15
Dec 30 11:22:21 gorky postfix/master[1653]: daemon started -- version 2.6.5, configuration /etc/postfix
Dec 30 11:22:22 gorky dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Dec 30 11:22:55 gorky postfix/master[1653]: reload -- version 2.6.5, configuration /etc/postfix
Dec 30 11:23:25 gorky dovecot: Killed with signal 15
paul@gorky:/var/log$ cat mail.log
Dec 29 12:17:27 gorky postfix/master[1692]: daemon started -- version 2.6.5, configuration /etc/postfix
Dec 29 12:17:30 gorky dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Dec 29 12:18:28 gorky postfix/master[1692]: reload -- version 2.6.5, configuration /etc/postfix
Dec 29 21:26:38 gorky dovecot: imap-login: Login: user=<paul>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Dec 29 21:27:58 gorky dovecot: Killed with signal 15
Dec 30 11:22:21 gorky postfix/master[1653]: daemon started -- version 2.6.5, configuration /etc/postfix
Dec 30 11:22:22 gorky dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Dec 30 11:22:55 gorky postfix/master[1653]: reload -- version 2.6.5, configuration /etc/postfix
Dec 30 11:23:25 gorky dovecot: Killed with signal 15
paul@gorky:/var/log$ cat mail.warn
Dec 29 21:27:58 gorky dovecot: Killed with signal 15
Dec 30 11:23:25 gorky dovecot: Killed with signal 15
paul@gorky:/var/log$ cat mail.err
paul@gorky:/var/log$ 
```

---

