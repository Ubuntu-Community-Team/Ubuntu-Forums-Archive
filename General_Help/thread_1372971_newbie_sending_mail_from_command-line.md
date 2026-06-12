---
title: "newbie sending mail from command-line"
date: 2010-01-05
forum: General Help
---

### Post by davidtuti on 2010-01-05
Hi,

Hi,

I have kubuntu 9.10 and I would like to configure Ubuntu to can send mail from command line with mailx.
I've saw that I need to install a MTA. But I don't know wich install and how.

I follow this tutorial:

[http://www.ericstockwell.com/?p=3](http://www.ericstockwell.com/?p=3)

But when I try to send a message, in the mail.log says me:

```
Jan  5 10:21:33 david postfix/smtp[3795]: 41AEA41DBE: to=<pepelu@gmail.com>, relay=alt1.gmail-smtp-in.l.google.com[209.85.223.73]:25, delay=1086, d
elays=1022/0.01/32/32, dsn=4.7.0, status=deferred (host alt1.gmail-smtp-in.l.google.com[209.85.223.73] said: 421-4.7.0 [95.16.242.150] Our system has
detected an unusual amount of 421-4.7.0 unsolicited mail originating from your IP address. To protect our 421-4.7.0 users from spam, mail sent from yo
ur IP address has been temporarily 421-4.7.0 blocked. Please visit http://www.google.com/mail/help/bulk_mail.html 421 4.7.0 to review our Bulk Email S
enders Guidelines. 5si31391479iwn.104 (in reply to end of DATA command))
Jan  5 10:23:44 david postfix/pickup[3437]: 2477C42290: uid=1000 from=<david>
Jan  5 10:23:44 david postfix/cleanup[3802]: 2477C42290: message-id=<20100105092344.2477C42290@david>
Jan  5 10:23:44 david postfix/qmgr[1585]: 2477C42290: from=<david@david>, size=295, nrcpt=1 (queue active)
```

Please any help?
Many thnaks and sorry for my english!

---

### Post by audiomick on 2010-01-05
Looks like you have been blocked.
```
Jan  5 10:21:33 david postfix/smtp[3795]: 41AEA41DBE: to=<pepelu@gmail.com>, relay=alt1.gmail-smtp-in.l.google.com[209.85.223.73]:25, delay=1086, d
elays=1022/0.01/32/32, dsn=4.7.0, status=deferred (host alt1.gmail-smtp-in.l.google.com[209.85.223.73] said: 421-4.7.0 [95.16.242.150] [B][COLOR="Red"]Our system has
detected an unusual amount of 421-4.7.0 unsolicited mail originating from your IP address. To protect our 421-4.7.0 users from spam, mail sent from yo
ur IP address has been temporarily 421-4.7.0 blocked[/COLOR][/B]. Please visit [http://www.google.com/mail/help/bulk_mail.html](http://www.google.com/mail/help/bulk_mail.html) 421 4.7.0 to review our Bulk Email S
enders Guidelines. 5si31391479iwn.104 (in reply to end of DATA command))
Jan  5 10:23:44 david postfix/pickup[3437]: 2477C42290: uid=1000 from=<david>
Jan  5 10:23:44 david postfix/cleanup[3802]: 2477C42290: message-id=<20100105092344.2477C42290@david>
Jan  5 10:23:44 david postfix/qmgr[1585]: 2477C42290: from=<david@david>, size=295, nrcpt=1 (queue active)
```

---

### Post by davidtuti on 2010-01-05
> **audiomick said:**
> Looks like you have been blocked.
```
Jan  5 10:21:33 david postfix/smtp[3795]: 41AEA41DBE: to=<pepelu@gmail.com>, relay=alt1.gmail-smtp-in.l.google.com[209.85.223.73]:25, delay=1086, d
elays=1022/0.01/32/32, dsn=4.7.0, status=deferred (host alt1.gmail-smtp-in.l.google.com[209.85.223.73] said: 421-4.7.0 [95.16.242.150] [B][COLOR="Red"]Our system has
detected an unusual amount of 421-4.7.0 unsolicited mail originating from your IP address. To protect our 421-4.7.0 users from spam, mail sent from yo
ur IP address has been temporarily 421-4.7.0 blocked[/COLOR][/B]. Please visit [http://www.google.com/mail/help/bulk_mail.html](http://www.google.com/mail/help/bulk_mail.html) 421 4.7.0 to review our Bulk Email S
enders Guidelines. 5si31391479iwn.104 (in reply to end of DATA command))
Jan  5 10:23:44 david postfix/pickup[3437]: 2477C42290: uid=1000 from=<david>
Jan  5 10:23:44 david postfix/cleanup[3802]: 2477C42290: message-id=<20100105092344.2477C42290@david>
Jan  5 10:23:44 david postfix/qmgr[1585]: 2477C42290: from=<david@david>, size=295, nrcpt=1 (queue active)
```

But I dont understand this! I have well configured with my ubuntu 9.04. 
Any help?

---

### Post by davidtuti on 2010-01-05
I see by google that it seems that the error doesnt have a easy solution.
Could you say me other way to can send mail from command-line?

Many thanks!

---

