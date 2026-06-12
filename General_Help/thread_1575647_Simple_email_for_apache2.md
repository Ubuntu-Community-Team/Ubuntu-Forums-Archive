---
title: "Simple email for apache2"
date: 2010-09-16
forum: General Help
---

### Post by dananimal on 2010-09-16
I am trying to set up ubuntu to run ResourceSpace DAM.

Almost everything is going great. But…

I can't get past an error from apache trying to send emails.

The network environment this machine is in has a MS Exchange server handling email.

I want to send all email though that mailserver.

Right now the apache2 user www-data tries to send by a local postfix MTA and fails:

```
Sep 16 15:55:20 ubuntu postfix/pickup[21028]: 1057645AE6: uid=33 from=<www-data>
Sep 16 15:55:20 ubuntu postfix/cleanup[21037]: 1057645AE6: message-id=<20100916055520myDomainUserName@myDomain.com>
Sep 16 15:55:20 ubuntu postfix/qmgr[21029]: 1057645AE6: from=<www-data@myDomain.com>, size=677, nrcpt=1 (queue active)
Sep 16 15:55:20 ubuntu postfix/local[21039]: 1057645AE6: to=<myDomainUserName@myDomain.com>, relay=local, delay=0.09, delays=0.06/0.01/0/0.01, dsn=5.1.1, status=bounced (unknown user: "myDomainUserName")
Sep 16 15:55:20 ubuntu postfix/cleanup[21037]: 1E51D45B9D: message-id=<20100916055520.1E51D45B9D@localhost>
Sep 16 15:55:20 ubuntu postfix/bounce[21040]: 1057645AE6: sender non-delivery notification: 1E51D45B9D
Sep 16 15:55:20 ubuntu postfix/qmgr[21029]: 1E51D45B9D: from=<>, size=2336, nrcpt=1 (queue active)
Sep 16 15:55:20 ubuntu postfix/qmgr[21029]: 1057645AE6: removed
Sep 16 15:55:20 ubuntu postfix/local[21039]: 1E51D45B9D: to=<www-data@myDomain.com>, relay=local, delay=0.01, delays=0/0/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
Sep 16 15:55:20 ubuntu postfix/qmgr[21029]: 1E51D45B9D: removed
```
The edited bits of /etc/postfix/main.cf in use:
```

myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
#myorigin = /etc/mailname
myorigin = tso.com.au
mydestination = smtp.myDomain.com, myDomain.com, localhost
relayhost = [haydn.tso.com.au]
mynetworks = 127.0.0.0/8 192.168.4.0/255 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
default_transport = error
relay_transport = error

```

I just want to send email via the existing email server.

Anyone able to assist?
Thanks in advance
;D

---

### Post by dananimal on 2010-09-16
I reinstalled postfix

```
sudo apt-get remove postfix --purge
sudo apt-get install postfix
```

Then set up as 'satellite system' choosing localhost as the hostname and smtp.myDomain.com as the relayhost.

It now seems to work.

Would still like any advice on the error of my ways.
;D

---

