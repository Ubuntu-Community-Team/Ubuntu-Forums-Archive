---
title: "Courier IMAP login error"
date: 2009-11-23
forum: General Help
---

### Post by barthel on 2009-11-23
I'm setting up postfix from scratch in Karmic. I followed [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) and am now working my way through [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

My first "gotcha" was when I attempted to do the first test for
"netcat mail.yourdomain.com 25", like so:

```
$ netcat mail.calainar 25
mail.calainar: forward host lookup failed: Unknown host : Connection timed out
```

The test works if I drop the "mail." portion, so I proceeded with the HowTo.

Courier POP3 tested successfully, but with Courier IMAP I get the following:
```
netcat calainar 143
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION] Courier-IMAP ready. Copyright 1998-2008 Double Precision, Inc.  See COPYING for distribution information.
login barthel <mypasswd>
login NO Error in IMAP command received by server.
```

Google and forum searches lead me to believe that it's an authorization issue, but I found nothing to lead me to enlightenment.

Here's my /etc/postfix/main.cf:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

myhostname = calainar
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = calainar, localhost.localdomain, , localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
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
home_mailbox = Maildir/

```

Any ideas how I can address the login error and proceed to the next step in the HowTo?

My #1 goal is to get my cron scripts working again. (I'm pretty sure the problem was the lack of an MTA on my Karmic installation.)

My #2 goal is to get the linux counter machine-update script emailing again. (I had it working for years with sendmail on Slackware, but I haven't yet got it working with Postfix.)

---

### Post by barthel on 2009-11-25
*bump*

#1 goal is accomplished, even though I haven't gotten any farther with Courier IMAP. My cron scripts are running correctly again, now that there is an MTA running.

---

### Post by fubes2000 on 2009-12-02
Not so much an answer as another question, but which mail service are you actually using? You keep switching names between Postfix and Courier...

---

