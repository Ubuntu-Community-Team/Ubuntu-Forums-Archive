---
title: "relay via isp problem 550 Authentication required"
date: 2012-07-07
forum: General Help
---

### Post by AlexBooton on 2012-07-07
Hi,

I'm getting dizzy from googling for this problem. :rolleyes:

I'm trying to relay mail through my isp (comcast.net).

I think it's basically set up correctly but I don't know why I can't get past this issue.  Syslog says:  
```
Jul  6 23:21:53 pti-server postfix/pickup[16558]: 15310CA01C5: uid=0 from=<ed@<my private domain>>
Jul  6 23:21:53 pti-server postfix/cleanup[16917]: 15310CA01C5: message-id=<1341631313.16936@<my private domain>>
Jul  6 23:21:53 pti-server postfix/qmgr[16559]: 15310CA01C5: from=<ed@<my private domain>>, size=387, nrcpt=2 (queue active)
Jul  6 23:21:54 pti-server postfix/smtp[16918]: certificate verification failed for smtp.comcast.net[76.96.30.117]:587: untrusted issuer /C=US/O=VeriSign, Inc./OU=Class 3 Public Primary Certification Authority
Jul  6 23:21:54 pti-server postfix/smtp[16918]: 15310CA01C5: to=<edh@example.com>, relay=smtp.comcast.net[76.96.30.117]:587, delay=1.7, delays=0.16/0/1.4/0.14, dsn=5.1.0, status=bounced (host smtp.comcast.net[76.96.30.117] said: 550 5.1.0 Authentication required (in reply to MAIL FROM command))
Jul  6 23:21:55 pti-server postfix/cleanup[16917]: F3465CA01C6: message-id=<20120707032154.F3465CA01C6@<my private domain>>
Jul  6 23:21:55 pti-server postfix/qmgr[16559]: F3465CA01C6: from=<>, size=2203, nrcpt=1 (queue active)
Jul  6 23:21:55 pti-server postfix/bounce[16922]: 15310CA01C5: sender non-delivery notification: F3465CA01C6
Jul  6 23:21:55 pti-server postfix/qmgr[16559]: 15310CA01C5: removed
Jul  6 23:21:55 pti-server postfix/smtp[16918]: certificate verification failed for smtp.comcast.net[76.96.30.117]:587: untrusted issuer /C=US/O=VeriSign, Inc./OU=Class 3 Public Primary Certification Authority
Jul  6 23:21:56 pti-server postfix/smtp[16918]: F3465CA01C6: to=<ed@<my private domain>>, relay=smtp.comcast.net[76.96.30.117]:587, delay=1.5, delays=0.1/0/1.3/0.11, dsn=5.1.0, status=bounced (host smtp.comcast.net[76.96.30.117] said: 550 5.1.0 Authentication required (in reply to MAIL FROM command))
Jul  6 23:21:56 pti-server postfix/qmgr[16559]: F3465CA01C6: removed
```

I'm not sure what that all means but think comcast doesn't trust me.  Why not?  I'm a reliable guy.

I have a hunch that comcast wants to see it's own domain in the message so I set these two items in main.cf

```
smtpd_banner = comcast.net ESMTP $mail_name (Ubuntu)
smtpd_sasl_local_domain = comcast.net
```
but to be honest I don't know what these two directives really do.

I have a further hunch that comcast doesn't like 
```

myhostname = pti.server
```
which is not a real domain.

Any help?

Thanks!

---

