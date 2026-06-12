---
title: "Postfix Woes"
date: 2010-10-01
forum: General Help
---

### Post by bumpo on 2010-10-01
I'm trying to set up email on my Ubuntu server and am running into a bit of trouble. Finally got SMTP to work but cant receive. using Postfix, Dovecot heres the error from the log: 

NOQUEUE: reject: RCPT from mail-qy0-f172.google.com[209.85.216.172]: 550 5.1.1 <test@velocibytes.com>: Recipient address rejected: User unknown in local recipient table; from=<wmo@domain.net> to=<test@velocibytes.com> proto=ESMTP helo=<mail-qy0-f172.google.com>

heres my postconf -n: 

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
mailbox_size_limit = 0
mydestination = velocibytes.com, mail.velocibytes.com, ve.veserver.com, localhost.veserver.com, localhost, $mydomain
mydomain = velocibytes.com
myhostname = velocibytes.comm
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = velocibytes.com
smtpd_sasl_security_options = noanonymous
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

The actual bounce message claims the "User is unknown." Any ideas?

---

### Post by SeijiSensei on 2010-10-01
You don't have a user named "test" on the server, nor an alias for "test".

---

### Post by bumpo on 2010-10-01
The user is on the system, it exists int the sasldb2 and in the Mail dir.

---

### Post by SeijiSensei on 2010-10-01
Does the user exist in /etc/passwd?  If not, try adding it there.

What if you try sending a message to user test from the command prompt with the mail command?  (Install the bsd-mailx package if it's not already installed.)

echo 'this is a test' | mail -s test test

Is that delivered?

I'm not a Postfix expert; I use sendmail.  Beyond these few obvious possibilities, you'll need a Postfix+SASL expert.

---

### Post by dcstar on 2010-10-02
> **bumpo said:**
> I'm trying to set up email on my Ubuntu server and am running into a bit of trouble. Finally got SMTP to work but cant receive. using Postfix, Dovecot heres the error from the log: 

NOQUEUE: reject: RCPT from mail-qy0-f172.google.com[209.85.216.172]: 550 5.1.1 <test@velocibytes.com>: Recipient address rejected: User unknown in local recipient table; from=<wmo@domain.net> to=<test@velocibytes.com> proto=ESMTP helo=<mail-qy0-f172.google.com>

heres my postconf -n: 

........
mydomain = velocibytes.com
myhostname = velocibytes.**comm**
.......

The actual bounce message claims the "User is unknown." Any ideas?

It would probably be better if **you** could spell correctly.

---

### Post by bumpo on 2010-11-23
Thanks for your kind words David. I have corrected the error but alas, still no messages. (Sorry for my absence, had a family emergency to attend to) 

postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
mailbox_size_limit = 0
mydestination = velocibytes.com, mail.velocibytes.com, ve.veserver.com, localhost.veserver.com, localhost, $mydomain
mydomain = velocibytes.com
myhostname = velocibytes.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = velocibytes.com
smtpd_sasl_security_options = noanonymous
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

---

### Post by dcstar on 2010-11-24
> **bumpo said:**
> Thanks for your kind words David. I have corrected the error but alas, still no messages. (Sorry for my absence, had a family emergency to attend to) 
........

Now that you actually have a correct config file, e-mails to that test account are now accepted.

---

### Post by bumpo on 2010-11-26
Well, the messages are indeed being accepted, thank you. However, I am not able to access them. It seems that PAM will not authenticate the users, even though the users exist in passwd and the log ins are correct.

---

