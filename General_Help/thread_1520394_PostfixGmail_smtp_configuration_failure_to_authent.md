---
title: "Postfix/Gmail smtp configuration: failure to authenticate and create a tls connection"
date: 2010-06-29
forum: General Help
---

### Post by BJenks22446 on 2010-06-29
I'm trying to configure postfix on an ubuntu virtual machine to use gmail as a relay client. For the past two days I have been in and out of the logs, changing parameters and blindly following tutorials but I can't get anything to work properly. So far I've narrowed my problems down to tls connection establishing and a failure to authenticate, judging by the local emails I've received from "The mail system". any help would be greatly appreciated, or even a redirection to a better location to post this thread, sorry, I'm new to forums. Thanks ahead of time. :]

/var/log/mail.warn

```
Jun 29 12:45:38 ubuntu postfix/local[1384]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Jun 29 12:45:38 ubuntu postfix/tlsmgr[1387]: warning: request to update table btree:/etc/postfix/smtp_scache in non-postfix directory /etc/postfix
Jun 29 12:45:38 ubuntu postfix/tlsmgr[1387]: warning: redirecting the request to postfix-owned data_directory /var/lib/postfix
```/var/log/mail.log

```
Jun 29 12:43:10 ubuntu postfix/master[1054]: daemon started -- version 2.7.0, configuration /etc/postfix
Jun 29 12:45:38 ubuntu postfix/pickup[1060]: 71DE942C5F: uid=1000 from=<user>
on established tJun 29 12:45:38 ubuntu postfix/cleanup[1381]: 71DE942C5F: message-id=<20100629164538.71DE942C5F@ubuntu.localdomain>
Jun 29 12:45:38 ubuntu postfix/qmgr[1061]: 71DE942C5F: from=<user@ubuntu.localdomain>, size=382, nrcpt=2 (queue active)
Jun 29 12:45:38 ubuntu postfix/local[1384]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Jun 29 12:45:38 ubuntu postfix/local[1384]: 71DE942C5F: to=<test@ubuntu.localdomain>, relay=local, delay=0.37, delays=0.07/0.17/0/0.13, dsn=5.1.1, status=bounced (unknown user: "test")
Jun 29 12:45:38 ubuntu postfix/tlsmgr[1387]: warning: request to update table btree:/etc/postfix/smtp_scache in non-postfix directory /etc/postfix
Jun 29 12:45:38 ubuntu postfix/tlsmgr[1387]: warning: redirecting the request to postfix-owned data_directory /var/lib/postfix
Jun 29 12:45:40 ubuntu postfix/smtp[1385]: setting up TLS connection to smtp.gmail.com[74.125.91.109]:587
Jun 29 12:45:40 ubuntu postfix/smtp[1385]: certificate verification failed for smtp.gmail.com[74.125.91.109]:587: untrusted issuer /C=US/O=Equifax/OU=Equifax Secure Certificate Authority
Jun 29 12:45:40 ubuntu postfix/smtp[1385]: Untrusted TLS connection established to smtp.gmail.com[74.125.91.109]:587: TLSv1 with cipher RC4-MD5 (128/128 bits)
Jun 29 12:45:40 ubuntu postfix/smtp[1385]: 71DE942C5F: to=<bjenks22446@gmail.com>, relay=smtp.gmail.com[74.125.91.109]:587, delay=2.5, delays=0.07/0.36/2/0.03, dsn=5.5.1, status=bounced (host smtp.gmail.com[74.125.91.109] said: 530-5.5.1 Authentication Required. Learn more at                               530 5.5.1 http://mail.google.com/support/bin/answer.py?answer=14257 i10sm41034462qcb.17 (in reply to MAIL FROM command))
Jun 29 12:45:40 ubuntu postfix/cleanup[1381]: EBF5C42C63: message-id=<20100629164540.EBF5C42C63@ubuntu.localdomain>
Jun 29 12:45:40 ubuntu postfix/bounce[1386]: 71DE942C5F: sender non-delivery notification: EBF5C42C63
Jun 29 12:45:40 ubuntu postfix/qmgr[1061]: EBF5C42C63: from=<>, size=2710, nrcpt=1 (queue active)
Jun 29 12:45:40 ubuntu postfix/qmgr[1061]: 71DE942C5F: removed
Jun 29 12:45:40 ubuntu postfix/local[1384]: EBF5C42C63: to=<user@ubuntu.localdomain>, relay=local, delay=0.03, delays=0.01/0/0/0.01, dsn=2.0.0, status=sent (delivered to mailbox)
Jun 29 12:45:40 ubuntu postfix/qmgr[1061]: EBF5C42C63: removed
```postconf -n

```
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
readme_directory = no
relayhost = smtp.gmail.com:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_password
smtp_sasl_security_options = noanonymous
smtp_tls_CApath = /etc/postfix/certs
smtp_tls_loglevel = 1
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:/etc/postfix/smtp_scache
smtp_tls_session_cache_timeout = 3600s
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
```/etc/postfix/sasl_password

```
[smtp.gmail.com]:587    username:password
```/etc/postfix/relay_password

```
[smtp.gmail.com]:587    username:password
```The mail system

```
<test@ubuntu.localdomain>: unknown user: "test"

<username@gmail.com>: host smtp.gmail.com[74.125.91.109] said:
+530-5.5.1
    Authentication Required. Learn more at
+530
    5.5.1
+http://mail.google.com/support/bin/answer.py?answer=14257
    i10sm41034462qcb.17 (in reply to MAIL FROM command)
```

---

### Post by Kepesk on 2010-07-12
I have the exact same problem, almost word-for-word.  I'm completely stuck.  Does anyone have an idea on this?

---

### Post by tfultz33 on 2010-10-09
I have the same problem:

Caesar postfix/smtp[3369]: certificate verification failed for smtp.gmail.com[74.125.39.109]:587: untrusted issuer /C=US/O=Equifax/OU=Equifax Secure Certificate Authority
Oct  9 21:12:05 Caesar postfix/smtp[3369]: 8A939201A59: to=<edited.edited.com>, relay=smtp.gmail.com[74.125.39.109]:587, delay=118, delays=113/0.07/4/0.43, dsn=5.5.1, status=bounced (host smtp.gmail.com[74.125.39.109] said: 530-5.5.1 Authentication Required. Learn more at

I have no idea how to download and install the latestEquifax cert.

---

