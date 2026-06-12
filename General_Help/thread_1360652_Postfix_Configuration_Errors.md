---
title: "Postfix Configuration Errors"
date: 2009-12-21
forum: General Help
---

### Post by lynwode on 2009-12-21
Hi,
I have followed the doco at [https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix"). All went well until id did a restart of postfix and I received the following error:

root@homer:/etc/postfix# /etc/init.d/postfix restart
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ]
 * Starting Postfix Mail Transport Agent postfix                                postfix: fatal: /etc/postfix/postfix-script: No such file or directory                            [fail]

I have done some digging on google and the forums but can't find any answers - does anyone have any idea. 

The contents of the main.cf are below.

Cheers,
Tim.

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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.home.test.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = homer.home.test.com, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
default_transport = smtp
relay_transport = smtp
inet_protocols = all
myorigin = /etc/mailname
home_mailbox = Maildir/
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

---

### Post by lynwode on 2009-12-27
Solved by removing postfix and reinstalling - for some reason the postfix-script file did not get created the first time I installed.

---

