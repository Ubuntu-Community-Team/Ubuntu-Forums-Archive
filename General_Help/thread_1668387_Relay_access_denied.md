---
title: "Relay access denied"
date: 2011-01-16
forum: General Help
---

### Post by makapacs on 2011-01-16
Hi,

I am setting up mail server. I installed PostFix,DoveCot and i can send email in, but i cannot send email out. When i send email out it gives:
'Relay access denied'

I followed following tutorial to configure Postfix and SASL:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

I can send email directly via telnet (followed DavidPhillips post [http://www.linuxquestions.org/questions/linux-software-2/postfix-cannot-send-e-mail-186776/](http://www.linuxquestions.org/questions/linux-software-2/postfix-cannot-send-e-mail-186776/)), but no from client neither Outlook nor squirrelmail

 Here is my postfix configuration:
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

#readme_directory = no

# TLS parameters
#smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#smtpd_use_tls=yes
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = maydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.mydomain.com, mydomain.com, localhost.mydomain.com, localhost
relayhost =
mynetworks = 127.0.0.0/8,70.xx.xx.194
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
myorigin = /etc/mailname
inet_protocols = all
#home_mailbox = Maildir/
mailbox_command =
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
#smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

Thank you for helping

Margots

---

