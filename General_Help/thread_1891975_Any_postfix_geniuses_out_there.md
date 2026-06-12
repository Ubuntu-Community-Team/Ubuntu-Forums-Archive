---
title: "Any postfix geniuses out there?"
date: 2011-12-07
forum: General Help
---

### Post by harty83 on 2011-12-07
I have a web server setup over at Linode with Ubuntu 10.04 LTS.  I used Virtualmin's install script to install everything needed to run the server.

Sometime recently, my email (google apps) quit delivering email sent from my server.  Looking in mail.log, the status is sent but it is never received in my inbox.  Searched trash, spam, etc and it is nowhere.  Its like Google accepts it but then decides to trash or ignore it without delivering it.  


> Dec  7 04:28:44 server postfix/qmgr[6674]: 88CD540D15: from=<myuser@server.mydomain.com>, size=1412, nrcpt=1 (queue active)
Dec  7 04:28:45 server postfix/smtp[13067]: 88CD540D15: to=<mypersonalemail@mydomain.com>, relay=alt1.aspmx.l.google.com[74.125.113.26]:25, delay=0.99, delays=0.28/0/0.15/0.55, dsn=2.0.0, status=sent (250 2.0.0 OK 1323232125 t7si71446vcw.7)

Any ideas on how to remedy this?

Thanks!
Alan

---

### Post by dcstar on 2011-12-08
> **harty83 said:**
> 
.........
Any ideas on how to remedy this?

Thanks!
Alan

Noting to do with Postfix, talk to Google and ask them about their Spam filtering.

---

