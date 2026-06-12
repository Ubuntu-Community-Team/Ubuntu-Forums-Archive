---
title: "Cannot send mail from personal server (Postfix)"
date: 2009-08-04
forum: General Help
---

### Post by Nexusx6 on 2009-08-04
Hello,

So, for a while now I've been trying to set up my home server to handle email for my domain using Postfix. I'm using an IP-Redirect service (No-Ip) that automatically updates my IP to a DNS. Also, I use imap-courier to handler Maildir and incoming mail.

Now, the imap-courier appears to be working, well, flawlessly. I send mail from gmail or wherever, and it shows up on my server within the a second. The problem however, is that I can't do the reverse -- I simply cannot send mail *out* from the server :( Using the mail program in terminal I can send mail to myself within the LAN, but as soon as I point it outside of the LAN, it simply never shows up :confused: There's no error message, the email doesn't get redirected to gmail's spam folder (I check everytime I test this)... it just vanishes. 

I tried using different email clients like Thunderbird and KMail; again, they can query the imap service just fine, but they can't send anything, returning various error's reporting the SMTP server has timed out.

I've tried pretty much everything, and from what I'm seeing Postfix looks to be configured properly. I have ports open for SMTP at port 25 and I can telnet in from diffrent computers no on the Lan to port 25, so it doesn't look like my ISP is blocking the port (AT&T). Here's my config file and ehlo localhost from my machine:

```
~$: telnet teamchaos.sytes.net 25
Trying 76.193.78.39...
Connected to teamchaos.sytes.net.
Escape character is '^]'.
220 teamchaos.sytes.net ESMTP Postfix (Ubuntu)
ehlo localhost 25
250-teamchaos.sytes.net
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

```
```
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

myhostname = teamchaos.sytes.net
alias_maps = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = teamchaos.sytes.net, TheLibrary, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8, 192.168.1.0/24
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
mailbox_command =

```

---

### Post by Nexusx6 on 2009-08-04
bump

---

