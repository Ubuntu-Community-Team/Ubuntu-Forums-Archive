---
title: "Postfix sending as root"
date: 2012-06-15
forum: General Help
---

### Post by egrimisu on 2012-06-15
Ho guys,
i configured postfix as a satelite so backuppc to be able to send mail regarding their backups. It's been working for 2 years now and i'm very happy with it

here are the used settings:


```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version
A

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = BackupPC.localdomain.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = 
relayhost = mail.externalmailserver.ro
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
inet_protocols = ipv4

# setari Misu
#smtp_sasl_auth_enable = yes
#smtpd_tls_auth_only = yes
#smtp_sasl_security_option = noanonymous
smtp_sasl_password_maps = hash:/etc/postfix/sasl_password
#virtual_alias_maps = hash:/etc/postfix/virtual
#virtual_alias_maps = hash:/etc/postfix/virtual
#smtp_generic_maps = hash:/etc/postfix/generic
#transport_maps = hash:/etc/postfix/transport
```


unfortunettly using: mail -s "test message" [email]myadress@yahoo.com[/email]


```
Jun 15 15:12:00 BackupPC postfix/pickup[4689]: 8413B30A12B0: uid=0 from=<root>
Jun 15 15:12:00 BackupPC postfix/cleanup[4694]: 8413B30A12B0: message-id=<20120615121200.8413B30A12B0@BackupPC.localdomain.local>
Jun 15 15:12:00 BackupPC postfix/qmgr[4690]: 8413B30A12B0: from=<**root@localdomain.local**>, size=338, nrcpt=1 (queue active)
Jun 15 15:12:05 BackupPC postfix/smtp[4696]: 8413B30A12B0: to=<egrimisu@yahoo.com>, relay=mail.externalmailserver[91.xxx.xxx.xxx]:25, delay=5.5, delays=0.35/0.01/0.05/5.1, dsn=5.7.1, status=bounced (host mail.externalmailserver[91.xxx.xxx.xxx] said: 550 5.7.1 Unable to relay (in reply to RCPT TO command))
```

why is the sistem sending the messange as [email]root@localdomain.local[/email] instead of my external mail address? how to change it?

---

### Post by btindie on 2012-06-15
That would be because you are sending it as user root... why do you think it should be sending it with a From of our own personal email address??

You can override what the mail command uses by setting a variable
```
env from="\"Homer Simpson\" <homer.simpson@gmail.com>" mail -s Test\ Message egrimisu@yahoo.com
```If you want it to be permanent then you can set it in the ~/.mailrc config file.
> set from="\"Homer Simpson\" <homer.simpson@gmail.com>"see:> man mail

---

