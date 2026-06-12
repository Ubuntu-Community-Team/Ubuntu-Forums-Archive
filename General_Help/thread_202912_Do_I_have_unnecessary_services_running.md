---
title: "Do I have unnecessary services running"
date: 2006-06-24
forum: General Help
---

### Post by mibadt on 2006-06-24
Hi,
Scanning my syslog while my PC has been completely idle, I noticed that once every 10 minutes the following logs are being written. Is this OK? Do I have unnecessary services running? How can I :clean  up" my future syslog?

------syslog segment written every 10 minutes----------
Jun 24 16:10:01 localhost postfix/qmgr[5279]: 9BF4050178: removed
Jun 24 16:16:04 localhost kernel: [4328787.023000] DROPPED IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:6e:94:36:18:08:00 SRC=10.0.0.3 DST=10.255.255.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=20912 PROTO=UDP SPT=138 DPT=138 LEN=209
Jun 24 16:17:01 localhost /USR/SBIN/CRON[25123]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jun 24 16:20:01 localhost /USR/SBIN/CRON[25197]: (root) CMD (. /usr/lib/lprfax/init && Do_Retries >/dev/null)
Jun 24 16:20:01 localhost postfix/pickup[23161]: AA5E150178: uid=0 from=<root>
Jun 24 16:20:01 localhost postfix/cleanup[25200]: AA5E150178: message-id=<20060624132001.AA5E150178@localhost>
Jun 24 16:20:01 localhost postfix/qmgr[5279]: AA5E150178: from=<root@localhost>, size=512, nrcpt=1 (queue active)
Jun 24 16:20:01 localhost postfix/local[25202]: AA5E150178: to=<miki@localhost>, orig_to=<root>, relay=local, delay=0, status=sent (delivered to mailbox)
---------------end---------------


TIA
:)

---

### Post by taurus on 2006-06-24
If you don't plan to use your machine to send mail or receive mail, then don't have to run postfix!

---

### Post by aysiu on 2006-06-24
You might want to try this:

1. [Enable extra repositories](http://www.psychocats.net/ubuntu/sources)
2. Install and use BUM: ```
sudo aptitude update
sudo aptitude install bum gksu
gksudo bum
``` and disable the unnecessary services.

---

### Post by scxtt on 2006-06-24
i don't see anything out of the ordinary in there ...

---

### Post by mibadt on 2006-06-24
Thanks all!
I used bum to stop some services;) 

[QUOTE=scxtt]i don't see anything out of the ordinary in there ...[/QUOTE]

---

### Post by FredB on 2006-06-25
Thanks for BUM. Never heard of it before. Great little tool ;)

---

### Post by hariprs on 2008-04-10
> **aysiu said:**
> You might want to try this:

1. [Enable extra repositories](http://www.psychocats.net/ubuntu/sources)
2. Install and use BUM: ```
sudo aptitude update
sudo aptitude install bum gksu
gksudo bum
``` and disable the unnecessary services.

Thanks a lot, this works for me..

---

