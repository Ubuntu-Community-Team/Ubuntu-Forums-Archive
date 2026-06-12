---
title: "postfix/sendmail issues"
date: 2006-05-11
forum: General Help
---

### Post by maino82 on 2006-05-11
i recently upgraded to apache 2.2.2 and php 5.1.4 and since then sendmail and postfix have been acting up. generally, the messages produce a "deferred transport" error, and when i do a "sudo postfix flush" it attempts to send the message but then times out. here's a section of the output from "mailq."

> -Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
5198C2006A7      298 Thu May 11 23:00:44  [email]www-data@gmail.com[/email]
                   (connect to gmail.com[216.239.57.83]: Connection timed out)
                                         [email]XXXXXXXX@gmail.com[/email]

EDA812006D7    27868 Thu May 11 23:02:07  [email]logcheck@gmail.com[/email]
                          (delivery temporarily suspended: deferred transport)
                                         [email]XXXXXXXX@gmail.com[/email]

and here's a few lines from /var/log/mail.log:

> May 11 23:00:44 localhost postfix/pickup[8280]: 5198C2006A7: uid=33 from=<www-data>
May 11 23:00:44 localhost postfix/cleanup[8362]: 5198C2006A7: message-id=<20060512030044.5198C2006A7@server1>
May 11 23:00:44 localhost postfix/qmgr[8281]: 5198C2006A7: from=<XXXXXXXXXX@gmail.com>, size=298, nrcpt=1 (queue active)
May 11 23:00:44 localhost postfix/qmgr[8281]: 5198C2006A7: to=<XXXXXXXXXX@gmail.com>, relay=none, delay=0, status=deferred (delivery temporarily suspended: deferred transport)
May 11 23:01:57 localhost postfix[8407]: error: to submit mail, use the Postfix sendmail command
May 11 23:01:57 localhost postfix[8407]: fatal: the postfix command is reserved for the superuser
May 11 23:02:01 localhost postfix/qmgr[8281]: 5198C2006A7: from=<www-data@gmail.com>, size=298, nrcpt=1 (queue active)
May 11 23:02:07 localhost postfix/pickup[8280]: EDA812006D7: uid=123 from=<logcheck>
May 11 23:02:07 localhost postfix/cleanup[8362]: EDA812006D7: message-id=<20060512030207.EDA812006D7@server1>
May 11 23:02:07 localhost postfix/qmgr[8281]: EDA812006D7: from=<logcheck@gmail.com>, size=27868, nrcpt=1 (queue active)
May 11 23:02:07 localhost postfix/qmgr[8281]: EDA812006D7: to=<root@gmail.com>, orig_to=<root>, relay=none, delay=0, status=deferred (delivery temporarily suspended: deferred transport)
May 11 23:02:31 localhost postfix/smtp[8460]: connect to gmail.com[64.233.171.83]: Connection timed out (port 25)
May 11 23:03:01 localhost postfix/smtp[8460]: connect to gmail.com[64.233.161.83]: Connection timed out (port 25)
May 11 23:03:31 localhost postfix/smtp[8460]: connect to gmail.com[216.239.57.83]: Connection timed out (port 25)
May 11 23:03:31 localhost postfix/smtp[8460]: 5198C2006A7: to=<david.maino@gmail.com>, relay=none, delay=167, status=deferred (connect to gmail.com[216.239.57.83]: Connection timed out)

i've tried everything that i could find on google, but my limited understanding of the inner workings of postfix and sendmail has prevented me from understanding any of what i've done so far, so i figured it was best to ask for help before i break things further. i'm guessing that i just need to configure it to properly communicate with gmail, but for the life of me i don't know how to do that. any help you could offer would be appreciated!

---

### Post by cyracks on 2006-05-12
It seems to me that this could be the problem
[QUOTE=maino82]
May 11 23:00:44 localhost postfix/qmgr[8281]: 5198C2006A7: to=<XXXXXXXXXX@gmail.com>, **relay=none**, delay=0,
[/QUOTE]

could you send the output of 
```

cat /etc/postfix/main.cf |grep [:alnum:]|grep -v ^#

```

---

### Post by maino82 on 2006-05-15
here's the output:

> ~$ cat /etc/postfix/main.cf |grep [:alnum:]|grep -v ^#
biff = no
append_dot_mydomain = no
myhostname = server1.imayknow.com
mydomain = imayknow.com
myorigin = $myhostname
smtpd_banner = $myhostname ESMTP $mail_name
smtp_sasl_auth_enable = yes
smtp_sasl_security_options =
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, localhost.$mydomain, localhost
relayhost =
relay_domains = $mydestination
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
defer_transports = smtp
disable_dns_lookups = yes
mailbox_command = procmail -a "$EXTENSION"
mynetworks = 127.0.0.0/8
mynetworks_style = host
masquerade_domains = server1.imayknow.com
masquerade_exceptions = root
local_recipient_maps =
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org, permit
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_alias_domains = imayknow.com
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
content_filter = amavis:[127.0.0.1]:10024
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_data_restrictions = reject_unauth_pipelining


thanks for your help!

---

