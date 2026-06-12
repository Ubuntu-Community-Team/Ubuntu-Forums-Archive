---
title: "Receiving messages with Postfix"
date: 2010-08-27
forum: General Help
---

### Post by JasonSwett on 2010-08-27
I installed and configured Postfix on my server and it seems to be working, at least to an extent. I can use telnet to send a message to [email]jason@mydomain.com[/email] and that works just fine. However, when I try to [email]jason@mydomain.com[/email] from GMail, I get an undeliverable message. What am I missing?

Thanks,
Jason

---

### Post by JasonSwett on 2010-08-28
I've made a new development. First of all, the domain I'm using is woollymammothlabs.com. Another domain that points to my server is li173-195.members.linode.com.

When I send a message from GMail to [email]jason@woollymammothlabs.com[/email], it doesn't work. When I send a message to [email]jason@li173-195.members.linode.com[/email], it works.

What do I need to do to make [email]jason@woollymammothlabs.com[/email] able to receive e-mails as well as [email]jason@li173-195.members.linode.com[/email]?

Thanks,
Jason

---

### Post by lisati on 2010-08-28
Have you included all the domains you receive mail for included in the "mydestination =" entry in Postifx's main.cf file?

---

### Post by JasonSwett on 2010-08-28
Yes. Here is my main.cf:

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

myhostname = woollymammothlabs.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = woollymammothlabs.com, li173-195.members.linode.com, localhost.members.linode.com, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
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

```

---

### Post by JasonSwett on 2010-08-30
If that's not it, does anyone know what else might be wrong?

---

