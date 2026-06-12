---
title: "postfix  relay"
date: 2011-08-15
forum: General Help
---

### Post by kerrywes on 2011-08-15
I need some help!

I run a charity and im trying to get Postfix working the problem is relayhost! wwhat    do i setthis to?\

currently i have:

root@westttorg:~# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = mail.westfallfoundation.org, localhost.localdomain, localhost
myhostname = mail.westfallfoundation.org
mynetworks = 192.168.0.0/24 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_path = private/auth-client
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
root@westttorg:~# 	
mail.westfallfoundation.org is my MX

output:
telnet mail.westfallfoundation.org 25
helo  mail.westfallfoundation.org
mail from:    <kerrywes@mal.westfallfoundation.org>                                                 
rcpt to: <kerrywes@GMAIL.com>

...
554 5.7.1 <kerrywes@somewhere.com>: Relay access denied

Can someone show me exactly  how  to fix this?

---

