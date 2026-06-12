---
title: "proxying postfix"
date: 2006-02-19
forum: General Help
---

### Post by Burke on 2006-02-19
I spent almost my entire day compiling postfix and related software only to find out that (I'm 80% sure) my ISP blocks outbound connections on port 25. 

So now I need to find some way to tunnel my postfix traffic. Conveniently enough, I have TOR installed and running 24/7, so that will work, if someone can clue me in on how to set up the proxification ;).

Thanks a ton in advance

---

### Post by Burke on 2006-02-19
If it helps, here's my /etc/postfix/main.cf

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = xxxxxxxxxxxxxxxxxxxxxxxxx
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost.localdomain, localhost.localdomain, localhost
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all


readme_directory = no
sample_directory = /etc/postfix
sendmail_path = /usr/sbin/sendmail
html_directory = no
setgid_group = postdrop
command_directory = /usr/sbin
manpage_directory = /usr/local/man
daemon_directory = /usr/libexec/postfix
newaliases_path = /usr/bin/newaliases
mailq_path = /usr/bin/mailq
queue_directory = /var/spool/postfix
mail_owner = postfix
unknown_local_recipient_reject_code = 450




    ## TLS Settings
    #
    # For no logs set = 0
    smtp_tls_loglevel = 1
    #
    # smtp_enforce_tls = yes
    # Above is commented because doing it site by site below
    smtp_tls_per_site = hash:/etc/postfix/tls_per_site
    #
    smtp_tls_CAfile = /etc/postfix/cacert.pem
    smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
    smtp_tls_key_file = /etc/postfix/FOO-key.pem
    smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
    smtp_use_tls = yes
    smtpd_tls_CAfile = /etc/postfix/cacert.pem
    smtpd_tls_cert_file = /etc/postfix/FOO-cert.pem
    smtpd_tls_key_file = /etc/postfix/FOO-key.pem
    smtpd_tls_received_header = yes
    smtpd_tls_session_cache_database = btree:/var/run/smtpd_tls_session_cache
    smtpd_use_tls = yes
    tls_random_source = dev:/dev/urandom

    ##  SASL Settings
    # This is going in to THIS server
    smtpd_sasl_auth_enable = no
    # We need this
    smtp_sasl_auth_enable = yes
    smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
    smtpd_sasl_local_domain = $myhostname
    smtp_sasl_security_options = noanonymous
    #smtp_sasl_security_options =
    smtp_sasl_tls_security_options = noanonymous
    smtpd_sasl_application_name = smtpd


    ## Gmail Relay
    relayhost = [smtp.gmail.com]

    ## Good for Testing
    # sender_bcc_maps = hash:/etc/postfix/bcc_table

    # Disable DNS Lookups
    disable_dns_lookups = yes
    #
    # Great New feature Address Mapping
    smtp_generic_maps = hash:/etc/postfix/generic
    #
    #
    transport_maps = hash:/etc/postfix/transport



```

---

### Post by Burke on 2006-02-19
Now I really don't know what to think.  Here's the output in /var/log/mail.info when I try to send mail with mutt.

```
Feb 19 19:45:28 burke postfix/pickup[12963]: E38D275034B: uid=1000 from=<xxxxxxxxxxxxxx@gmail.com>
Feb 19 19:45:28 burke postfix/cleanup[13899]: E38D275034B: message-id=<20060220014527.GA13891@burke.fake.com>
Feb 19 19:45:28 burke postfix/qmgr[10635]: E38D275034B: from=<xxxxxxxxxxxxxx@gmail.com>, size=416, nrcpt=1 (queue active)
Feb 19 19:45:58 burke postfix/smtp[13901]: connect to gmail-smtp-in.l.google.com[72.14.205.27]: Connection timed out (port 25)
Feb 19 19:45:58 burke postfix/smtp[13901]: connect to alt2.gmail-smtp-in.l.google.com[66.249.83.27]: No route to host (port 25)
Feb 19 19:45:58 burke postfix/smtp[13901]: connect to alt1.gmail-smtp-in.l.google.com[64.233.167.27]: No route to host (port 25)
Feb 19 19:45:58 burke postfix/smtp[13901]: connect to alt2.gmail-smtp-in.l.google.com[66.249.83.114]: No route to host (port 25)
Feb 19 19:46:19 burke postfix/qmgr[10635]: B25037500C7: from=<root@burke.fake.com>, size=434, nrcpt=1 (queue active)

```

Can anyone make sense of this?

**EDIT: Should it be connecting to port 587 or 465 for gmail, not 25?**

Thanks







**EDIT AGAIN:  Nevermind, figured it out. Options in main.cf can't be indented.**

---

