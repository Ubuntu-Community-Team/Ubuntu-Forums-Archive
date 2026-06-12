---
title: "Postfix SMTP broken (cannot connect to saslauthd server: No such file or directory)"
date: 2010-02-06
forum: General Help
---

### Post by jyou on 2010-02-06
I am running Ubuntu 8.04 LTS, this is a fairly fresh install with Virtualmin GPL and a few virtual hosts just recently installed.

The problem I'm having is users are unable to send mail using SMTP remotely.  The mail client would attempt connection, the connection is established but later fails and report that either the username or password are wrong (when they are in fact correct)

Using webmail hosted on the same server to send mail works without any problem.

Upon viewing the mail.log, I find the following messages:

[INDENT]Feb  6 14:27:09 h3o postfix/smtpd[4321]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Feb  6 14:27:09 h3o postfix/smtpd[4321]: warning: SASL authentication failure: Password verification failed
Feb  6 14:27:09 h3o postfix/smtpd[4321]: warning: unknown[12.34.56.78]: SASL PLAIN authentication failed: generic failure[/INDENT]

I have tried using testsaslauthd to test in an SSH session, and initially it fails:
[INDENT]root@server:~#  testsaslauthd -u testuser -p testpassword   
connect() : No such file or directory
[/INDENT]

But when I specify the socket path, it will work:
[INDENT]root@server:~#  testsaslauthd -u testuser -p testpassword -f /var/spooostfix/var/run/saslauthd/mux -s smtp
0: OK "Success."
[/INDENT]

Clients are remotely connecting through a non-standard SMTP port (2525), although port #25 is open as well, and here are the lines from /etc/postfix/master.cf:

[INDENT]smtp	inet	n	-	-	-	-	smtpd -o smtpd_sasl_auth_enable=yes
2525	inet	n	-	-	-	-	smtpd -o smtpd_sasl_auth_enable=yes
[/INDENT]

When using telnet to port 2525 to test the SMTP, here's what I get:
[INDENT]EHLO somehostname
250-some.mailserver.com
250-PIPELINING
250-SIZE 25000000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
AUTH PLAIN *<base64 encoded \0username\0password>*
535 5.7.8 Error: authentication failed: bad protocol / cancel
[/INDENT]

Also, below is my main.cf
[INDENT]# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = server.domain.com, localhost.domain.com, localhost, $myhostname, localhost.$mydomain
mailbox_size_limit = 0
recipient_delimiter = +
virtual_alias_maps = hash:/etc/postfix/virtual
sender_bcc_maps = hash:/etc/postfix/bcc
mailbox_command = /usr/bin/procmail-wrapper -o -a $DOMAIN -d $LOGNAME
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination
message_size_limit = 25000000
smtpd_tls_security_level = may

[/INDENT]

I'm not an expert in setting up mail servers, but it seems as saslauthd is not talking properly to postfix.  Any help is greatly appreciated, as I've been hacking at this for nearly the whole day now.  :-(

---

### Post by jyou on 2010-02-07
bump - Nobody has any idea?

---

### Post by dcstar on 2010-02-08
> **jyou said:**
> bump - Nobody has any idea?

So how many general Ubuntu users do you think set up SMTP servers with this?

This is a forum for General issues of people using their Ubuntu systems, not arcane specialist issues or any other issue someone just decides to post here.

Find a more appropriate forum to post this sort of thing and you may get it seen by people who do have something to contribute, searching out other postfix issues should provide clues.

---

### Post by rgunn on 2010-04-23
In response to the arrogant reply above I have EXACTLY the same issue...what a coincidence.

"arcane specialist issues" or just something you know nothing about.

ubuntu users host their own email services etc & provide vps services doing the same thing.

If I find the cause I am more than happy to post a response here.

---

### Post by tkoco on 2010-05-31
Looks like you have not set up the certificates (TLS segment). "snakeoil" certificates are not real. Just something plugged into the configuration for the sake of completeness - like a stub file which is used during the writing of a program.

> **jyou said:**
> I am running Ubuntu 8.04 LTS, this is a fairly fresh install with Virtualmin GPL and a few virtual hosts just recently installed.

The problem I'm having is users are unable to send mail using SMTP remotely.  The mail client would attempt connection, the connection is established but later fails and report that either the username or password are wrong (when they are in fact correct)

Using webmail hosted on the same server to send mail works without any problem.

Upon viewing the mail.log, I find the following messages:

[INDENT]Feb  6 14:27:09 h3o postfix/smtpd[4321]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Feb  6 14:27:09 h3o postfix/smtpd[4321]: warning: SASL authentication failure: Password verification failed
Feb  6 14:27:09 h3o postfix/smtpd[4321]: warning: unknown[12.34.56.78]: SASL PLAIN authentication failed: generic failure[/INDENT]

I have tried using testsaslauthd to test in an SSH session, and initially it fails:
[INDENT]root@server:~#  testsaslauthd -u testuser -p testpassword   
connect() : No such file or directory
[/INDENT]

But when I specify the socket path, it will work:
[INDENT]root@server:~#  testsaslauthd -u testuser -p testpassword -f /var/spooostfix/var/run/saslauthd/mux -s smtp
0: OK "Success."
[/INDENT]

Clients are remotely connecting through a non-standard SMTP port (2525), although port #25 is open as well, and here are the lines from /etc/postfix/master.cf:

[INDENT]smtp	inet	n	-	-	-	-	smtpd -o smtpd_sasl_auth_enable=yes
2525	inet	n	-	-	-	-	smtpd -o smtpd_sasl_auth_enable=yes
[/INDENT]

When using telnet to port 2525 to test the SMTP, here's what I get:
[INDENT]EHLO somehostname
250-some.mailserver.com
250-PIPELINING
250-SIZE 25000000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
AUTH PLAIN *<base64 encoded \0username\0password>*
535 5.7.8 Error: authentication failed: bad protocol / cancel
[/INDENT]

Also, below is my main.cf
[INDENT]# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = server.domain.com, localhost.domain.com, localhost, $myhostname, localhost.$mydomain
mailbox_size_limit = 0
recipient_delimiter = +
virtual_alias_maps = hash:/etc/postfix/virtual
sender_bcc_maps = hash:/etc/postfix/bcc
mailbox_command = /usr/bin/procmail-wrapper -o -a $DOMAIN -d $LOGNAME
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination
message_size_limit = 25000000
smtpd_tls_security_level = may

[/INDENT]

I'm not an expert in setting up mail servers, but it seems as saslauthd is not talking properly to postfix.  Any help is greatly appreciated, as I've been hacking at this for nearly the whole day now.  :-(

---

