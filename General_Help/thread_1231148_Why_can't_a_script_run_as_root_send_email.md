---
title: "Why can't a script run as root send email?"
date: 2009-08-04
forum: General Help
---

### Post by lightnb on 2009-08-04
I have a script that, when run by a normal user, sends out an email message.

But when I run it as root, either with sudo or the root crontab, the email doesn't send.  Why is that?

---

### Post by NETabuse on 2009-08-04
not sure if this is in anyway right for your situation but, maybe you have the MTA on your system setup with a no root user login directive? This is common on ftp servers and i think i've seen it some mail servers before.

otherwise, your question should come with alot more detail if you need help. Give us error messages from /var/log/mail.err /var/log/mail.log /var/log/mail.info   and any other settings, details, pastes of your /etc/[postfix|sendmail|exim]/main.cf files etc etc. 

the key thing is without knowing more about your environment nobody can be expected to help.

:) Don't take it as criticism, just take it as a lesson.

---

### Post by slakkie on 2009-08-04
Can you post the script?

And be aware that you need to set a PATH when running things from cron.

---

### Post by lightnb on 2009-08-04
I wanted to see if this was a deliberate Ubuntu "security" thing before posting more details.


The script in question:
```

#!/bin/bash
SUBJECT="Test Email"
TO="myemail@gmail.com"
MESSAGE="/tmp/message.txt"

echo "This is my message body" >> $MESSAGE

/usr/bin/mail -s "$SUBJECT" "$TO" < $MESSAGE

rm $MESSAGE

```


Postfix:
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
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/ssl/certs/mailcert.pem
smtpd_tls_key_file = $smtpd_tls_cert_file


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mysite.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = 
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-forwards.cf, mysql:/etc/postfix/mysql-email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000

proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps

```


mail.log
```

Aug  4 08:43:33 mail postfix/pickup[8463]: 60AB9F85C6: uid=0 from=<root>
Aug  4 08:43:33 mail postfix/cleanup[8720]: 60AB9F85C6: message-id=<20090804124333.60AB9F85C6@mysite.com>
Aug  4 08:43:33 mail postfix/qmgr[4224]: 60AB9F85C6: from=<root@mail.mysite.com>, size=366, nrcpt=1 (queue active)
Aug  4 08:43:33 mail postfix/smtp[8724]: 60AB9F85C6: to=<myemail@gmail.com>, relay=gmail-smtp-in.l.google.com[209.85.217.58]:25, delay=0.36, delays=0.07/0/0.08/0.21, dsn=2.0.0, status=sent (250 2.0.0 OK 1249389813 10si15408181gxk.3)
Aug  4 08:43:33 mail postfix/qmgr[4224]: 60AB9F85C6: removed

```

---

### Post by regala on 2009-08-04
> **lightnb said:**
> 
mail.log
```

Aug  4 08:43:33 mail postfix/pickup[8463]: 60AB9F85C6: uid=0 from=<root>
Aug  4 08:43:33 mail postfix/cleanup[8720]: 60AB9F85C6: message-id=<20090804124333.60AB9F85C6@mysite.com>
Aug  4 08:43:33 mail postfix/qmgr[4224]: 60AB9F85C6: from=<root@mail.mysite.com>, size=366, nrcpt=1 (queue active)
Aug  4 08:43:33 mail postfix/smtp[8724]: 60AB9F85C6: to=<myemail@gmail.com>, relay=gmail-smtp-in.l.google.com[209.85.217.58]:25, delay=0.36, delays=0.07/0/0.08/0.21, dsn=2.0.0, status=sent (250 2.0.0 OK 1249389813 10si15408181gxk.3)
Aug  4 08:43:33 mail postfix/qmgr[4224]: 60AB9F85C6: removed

```

well, looking at your logs, the mail was sent and ACCEPTED by the remote server
BUT
your mail contains no From: prior to sending. Thus, it is completed by a simple From: [email]root@mail.bidule.net[/email] which may be internally filtered at Gmail.com
You shouldn't use root@ to send mail over the Internet.

---

### Post by lightnb on 2009-08-05
OK, I added a "from" to my sendmail command in the script and it now works ok. Thanks for your help!

---

