---
title: "Nagios Email Notifications"
date: 2009-11-17
forum: General Help
---

### Post by cazter on 2009-11-17
I have Nagios installed and running perfectly on Ubuntu Jaunty but for the life of me I cannot manage to get email notifications to send out. I have installed Mailx/Postfix and was hoping to SMTP through my Exchange server (SSL Port 587) but I am getting absolutely nowhere. I have read as many articles and how-to's as Google can point me towards and at this point I am not sure where I stand in terms of the configuration.

Any help at all would be extremely appreciated!

---

### Post by cazter on 2009-11-17
bump :)

---

### Post by karlson on 2009-11-17
> **cazter said:**
> I have Nagios installed and running perfectly on Ubuntu Jaunty but for the life of me I cannot manage to get email notifications to send out. I have installed Mailx/Postfix and was hoping to SMTP through my Exchange server (SSL Port 587) but I am getting absolutely nowhere. I have read as many articles and how-to's as Google can point me towards and at this point I am not sure where I stand in terms of the configuration.

Any help at all would be extremely appreciated!

Can sendmail/telnet establish an outside connection?

---

### Post by cazter on 2009-11-17
Yes, "*220 Nagios-SLC ESMTP Postfix (Ubuntu)*."

Able to get right in on telnet from another internal box. Not sure what you mean by "sendmail."

---

### Post by cazter on 2009-11-18
I just want Postfix to push emails to my Exchange SMTP!

Here's a look at /etc/postfix/main.cf

[I]#myorigin = /etc/mailname

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

myhostname = Nagios-SLC
mydomain = nagios-slc.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = $mydomain, $myhostname
relayhost = smtp.mydomain.com
mynetworks = 192.168.3.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
myorigin = $mydomain
inet_protocols = ipv4
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
canonical_maps = hash:/etc/postfix/canonical[/I]

I have my "relayhost" setting set to my Exchange SMTP address but when I go to send an email via Telnet I get: 

*554 5.7.1 <nagios@mydomain.com>:** Relay access denied***

Thoughts?

---

