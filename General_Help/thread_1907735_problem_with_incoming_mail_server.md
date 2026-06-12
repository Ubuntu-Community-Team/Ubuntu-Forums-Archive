---
title: "problem with incoming mail server"
date: 2012-01-12
forum: General Help
---

### Post by rhyancute on 2012-01-12
hello,

after i setup ubuntu server 11.10
my send mail is okay but i can not receive emails

this is from my /var/log/mail.log 
```

Jan 12 09:38:30 malek dovecot: pop3-login: Disconnected (tried to use disabled plaintext auth): rip=192.168.1.1, lip=192.168.1.248
Jan 12 09:38:33 malek postfix/smtpd[6481]: connect from unknown[192.168.1.1]
Jan 12 09:38:33 malek postfix/smtpd[6481]: 0506A3C191A: client=unknown[192.168.1.1]
Jan 12 09:38:33 malek postfix/cleanup[6485]: 0506A3C191A: message-id=<>
Jan 12 09:38:33 malek postfix/qmgr[6256]: 0506A3C191A: from=<diansay@malek.co>, size=541, nrcpt=1 (queue active)
Jan 12 09:38:33 malek postfix/smtpd[6481]: disconnect from unknown[192.168.1.1]
Jan 12 09:38:33 malek postfix/local[6486]: 0506A3C191A: to=<diansay@malek.co>, relay=local, delay=0.15, delays=0.1/0/0/0.05, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jan 12 09:38:33 malek postfix/qmgr[6256]: 0506A3C191A: removed
Jan 12 09:41:53 malek postfix/anvil[6483]: statistics: max connection rate 2/60s for (smtp:192.168.1.1) at Jan 12 09:38:33
Jan 12 09:41:53 malek postfix/anvil[6483]: statistics: max connection count 1 for (smtp:192.168.1.1) at Jan 12 09:37:58
Jan 12 09:41:53 malek postfix/anvil[6483]: statistics: max cache size 1 at Jan 12 09:37:58

```

---

