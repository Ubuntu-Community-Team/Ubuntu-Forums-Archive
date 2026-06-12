---
title: "Postfix errors"
date: 2012-03-26
forum: General Help
---

### Post by hunterlove22 on 2012-03-26
I am using ispconf in Ec2 ubuntu. My email can not receive any email outside, just gets the below errors. 

```
Mar 26 21:13:12 sportsmanbids postfix/smtpd[17076]: [COLOR="Red"]warning: Illegal address syntax from localhost[127.0.0.1] in MAIL command[/COLOR]: <root@#skinnywaterproducts.com>
Mar 26 21:13:12 sportsmanbids postfix/error[17084]: 65E90103F5: to=<root@#skinnywaterproducts.com>, relay=none, delay=0.01, delays=0.01/0/0/0, dsn=5.1.3, status=bounced (bad address syntax)
Mar 26 21:13:12 sportsmanbids postfix/qmgr[17072]: 65E90103F5: removed
Mar 26 21:13:12 sportsmanbids postfix/smtpd[17090]: warning: Illegal address syntax from localhost[127.0.0.1] in MAIL command: <root@#skinnywaterproducts.com>
Mar 26 21:13:12 sportsmanbids amavis[17087]: (17087-01-2) Negative SMTP resp. to DATA: 503 5.5.1 Error: need RCPT command
Mar 26 21:13:12 [COLOR="red"]sportsmanbids amavis[17087]: (17087-01-2) (!)FWD via SMTP: <root@#skinnywaterproducts.com> -> [/COLOR]<kevin@sportsmanbids.com>,BODY=7BIT 501 5.1.7 Failed, id=17087-01-2, from MTA([127.0.0.1]:10025): 501 5.1.7 Bad sender address syntax
Mar 26 21:13:12 sportsmanbids amavis[17087]: (17087-01-2) Blocked MTA-BLOCKED, <root@#skinnywaterproducts.com> -> <kevin@sportsmanbids.com>, Message-ID: <20120323000410.1380B78C1E@sportsmanbids.com>, mail_id: cPSV5dY+iL60, Hits: 0.378, size: 627, 169 ms
Mar 26 21:13:12 sportsmanbids postfix/smtp[17074]: 1380B78C1E: to=<kevin@sportsmanbids.com>, relay=127.0.0.1[127.0.0.1]:10024, conn_use=2, delay=335343, delays=335332/10/0/0.17, dsn=5.1.7, status=bounced (host 127.0.0.1[127.0.0.1] said: 501 5.1.7 Failed, id=17087-01-2, from MTA([127.0.0.1]:10025): 501 5.1.7 Bad sender address syntax (in reply to end of DATA command))
Mar 26 21:13:12 sportsmanbids postfix/cleanup[17081]: 919B61032F: message-id=<20120326211312.919B61032F@webmail.sportsmanbids.com>
Mar 26 21:13:12 sportsmanbids postfix/bounce[17080]: 1380B78C1E: sender non-delivery notification: 919B61032F
Mar 26 21:13:12 sportsmanbids postfix/qmgr[17072]: 919B61032F: from=<>, size=2798, nrcpt=1 (queue active)
Mar 26 21:13:12 sportsmanbids postfix/qmgr[17072]: 1380B78C1E: removed
Mar 26 21:13:12 sportsmanbids postfix/error[17084]: 919B61032F: to=<root@#skinnywaterproducts.com>, relay=none, delay=0.04, delays=0.04/0/0/0, dsn=5.1.3, status=bounced (bad address syntax)
Mar 26 21:13:12 sportsmanbids postfix/qmgr[17072]: 919B61032F: removed
Mar 26 21:13:12 sportsmanbids postfix/smtpd[17090]: warning: Illegal address syntax from localhost[127.0.0.1] in MAIL command: <root@#skinnywaterproducts.com>
Mar 26 21:13:13 sportsmanbids amavis[17087]: (17087-01-3) Negative SMTP resp. to DATA: 503 5.5.1 Error: need RCPT command

```

Just also wonder why it is [email]root@[COLOR="red"]#[/COLOR]skinnywaterproducts.com[/email]. and how to remove it.

My main.cf:

> myhostname = webmail.sportsmanbids.com
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
alias_database = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
myorigin = /etc/mailname
mydestination = webmail.sportsmanbids.com, localhost, localhost.localdomain
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, proxy:mysql:/etc/postfix/mysql-virtual_email2email.cf, hash:/var/lib/mailman/data/v$
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_unaut$
smtpd_tls_security_level = may
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipie$
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
maildrop_destination_recipient_limit = 1
virtual_transport = dovecot
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
owner_request_special = no
dovecot_destination_recipient_limit = 1
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
smtpd_tls_CAfile = /usr/local/ispconfig/interface/ssl/startssl.chain.class1.server.crt




Thanks!

---

### Post by dcstar on 2012-03-27
> **hunterlove22 said:**
> I am using ispconf in Ec2 ubuntu. My email can not receive any email outside, just gets the below errors. 
.......
Just also wonder why it is [email]root@[COLOR="red"]#[/COLOR]skinnywaterproducts.com[/email]. and how to remove it.


```
man hostname
cat /etc/hosts
cat /etc/aliases
```

---

### Post by hunterlove22 on 2012-03-27
I checked all, but no strange!

---

