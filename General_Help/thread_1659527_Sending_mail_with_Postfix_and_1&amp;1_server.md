---
title: "Sending mail with Postfix and 1&amp;1 server"
date: 2011-01-04
forum: General Help
---

### Post by leemid on 2011-01-04
Hi all,

I'm working on a small website using PHP where I would like users to be able to send email. Since I have mail provided by my host 1&1, I thought it might be easier to have Postfix use 1&1's SMTP server rather than setting up my own. However... whenever I try to send mail from the PHP console I get the following error in my /var/log/mail.log:

```
Jan  4 11:49:13 mail postfix/smtp[9952]: CEEBC104677: to=<user@domain.org>, relay=auth.smtp.1and1.co.uk[212.227.15.179]:587, delay=2.4, delays=0.07/0/0.21/2.1, dsn=5.0.0, status=bounced (host auth.smtp.1and1.co.uk[212.227.15.179] said: **550 must be authenticated (in reply to RCPT TO command)**)
```

I have set up /etc/postfix/sasl_passwd to the best of my ability also, but there's obviously still something I'm doing wrong. If anyone has experience of sending mail from Postfix through 1&1 I'd be really grateful for your help!

Thanks,
Lee

Here are the contents of my /etc/postfix/main.cf:

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
relayhost = [auth.smtp.1and1.co.uk]:587
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
myorigin = /etc/mailname
inet_protocols = ipv4
smtpd_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtpd_recipient_restrictions = permit_mynetworks reject_unauth_destination permit_inet_interfaces permit_sasl_authenticated
smtpd_sasl_security_options = noanonymous
masquerade_domains = donotreply@domain.org

```

---

