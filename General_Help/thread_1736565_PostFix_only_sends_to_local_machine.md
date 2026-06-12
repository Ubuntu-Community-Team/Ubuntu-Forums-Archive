---
title: "PostFix only sends to local machine"
date: 2011-04-22
forum: General Help
---

### Post by NettSite on 2011-04-22
I am running PostFix as an MTA on an Ubuntu server with several websites using Apache. The websites need to send mail to confirm registrations, service "contact us" forms, etc.

This was all working beautifully but a problem has developed somehow and now PostFix will only send mail between email accounts on the server which PostFix is running on.

I need it to send mail "from" whatever account the visitor to the site enters in a form, to the account configured to receive the "contact us" info, for example, or from the website's admin email address (which is hosted elsewhere, not on the same server) to the email address of the newly registered person.

I realise that PostFix is trying to prevent being abused to send spam or something, but I do need a little leeway here!

The server is a virtual one, with fixed IP address.

Would appreciate any help.

---

### Post by figure002 on 2011-09-22
I also would like to know how to do this. I had this working with Postfix in the past, but now that I got a Ubuntu Server I can't get it to work. I can send emails locally, but not to external destinations.

My configuration:
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = cyrax
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = cyrax, localhost.localdomain, , localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
myorigin = /etc/mailname

```

In the above "cyrax" is the hostname of my server.

---

