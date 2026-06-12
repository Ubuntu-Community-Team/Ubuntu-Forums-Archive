---
title: "/etc/postfix/virtual file missing"
date: 2010-08-29
forum: General Help
---

### Post by 10ghost on 2010-08-29
I am following a mail server r configuration by 
[http://flurdy.com/docs/postfix/#test](http://flurdy.com/docs/postfix/#test)

I observed that i need a /etc/postfix/virtual and noticed it is not my system
When trying to test basic mail server configuration
telnet FQDN(fully qualified domain name) 25
it gives the error
```

telnet: could not resolve hostname/25: Name or service not known

```
 but when i change the FQDN to localhost it works fine.

I check the mail.log file and observe the following errors

```

to=<glider@smtp.oladeleodugbemi.net>, relay=none, delay=16426, delays=16426/0.14/0/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=smtp.oladeleodugbemi.net type=MX: Host not found, try again)
Aug 29 22:08:35 (none) postfix/smtp[4613]: ACA87E14DE: to=<glider@smtp.oladeleodugbemi.net>, relay=none, delay=16426, delays=16426/0.16/0/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=smtp.oladeleodugbemi.net type=MX: Host not found, try again)
Aug 29 22:08:35 (none) postfix/smtp[4611]: AF50EE14DF: to=<root@smtp.oladeleodugbemi.net>, orig_to=<root>, relay=none, delay=37978, delays=37977/0.15/0/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=smtp.oladeleodugbemi.net type=MX: Host not found, try again)
Aug 29 22:08:35 (none) postfix/smtp[4609]: BFAA5E14D6: to=<root@smtp.oladeleodugbemi.net>, orig_to=<root>, relay=none, delay=38003, delays=38003/0.14/0/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=smtp.oladeleodugbemi.net type=MX: Host not found, try again)
Aug 29 22:08:37 (none) postfix/master[1933]: reload -- version 2.7.0, configuration /etc/postfix
Aug 29 22:08:37 (none) postfix/qmgr[4681]: BFAA5E14D6: from=<glider@smtp.oladeleodugbemi.net>, size=470, nrcpt=1 (queue active)
Aug 29 22:08:37 (none) postfix/qmgr[4681]: AF50EE14DF: from=<glider@smtp.oladeleodugbemi.net>, size=470, nrcpt=1 (queue active)
Aug 29 22:08:37 (none) postfix/qmgr[4681]: ACA87E14DE: from=<>, size=2798, nrcpt=1 (queue active)
Aug 29 22:08:37 (none) postfix/qmgr[4681]: BEDCBE14E0: from=<>, size=2798, nrcpt=1 (queue active)
Aug 29 22:08:39 (none) postfix/smtp[4703]: ACA87E14DE: to=<glider@smtp.oladeleodugbemi.net>, relay=none, delay=16430, delays=16428/1/0.61/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=smtp.oladeleodugbemi.net type=AAAA: Host not found)
Aug 29 22:08:39 (none) postfix/qmgr[4681]: ACA87E14DE: removed
Aug 29 22:08:39 (none) postfix/smtp[4704]: BEDCBE14E0: to=<glider@smtp.oladeleodugbemi.net>, relay=none, delay=16430, delays=16428/1/0.66/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=smtp.oladeleodugbemi.net type=AAAA: Host not found)
Aug 29 22:08:39 (none) postfix/qmgr[4681]: BEDCBE14E0: removed
Aug 29 22:08:39 (none) postfix/smtp[4702]: AF50EE14DF: to=<root@smtp.oladeleodugbemi.net>, orig_to=<root>, relay=none, delay=37981, delays=37980/1/0.67/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=smtp.oladeleodugbemi.net type=AAAA: Host not found)
Aug 29 22:08:39 (none) postfix/cleanup[4713]: 941EEE14DE: message-id=<20100829210839.941EEE14DE@smtp.oladeleodugbemi.net>
Aug 29 22:08:39 (none) postfix/bounce[4709]: AF50EE14DF: sender non-delivery notification: 941EEE14DE
Aug 29 22:08:39 (none) postfix/qmgr[4681]: 941EEE14DE: from=<>, size=2576, nrcpt=1 (queue active)


```

---

