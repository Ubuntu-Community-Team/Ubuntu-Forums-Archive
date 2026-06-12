---
title: "trying to set up mail server"
date: 2010-11-11
forum: General Help
---

### Post by truthseer0 on 2010-11-11
so i'm trying to set up a mail server and i've made SOME progress and then started to have dramatic episodes of FAIL.
guides i tried following:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)
[https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)

trying to get all this working on a server i don't have physical access to, a VPS from HazeNET, and this is what i CAN do:
send mail from root to my gmail
send mail from gmail to root

both of those are only being done from being logged in via ssh.
i can't get it working with any external clients, or SquirrelMail for that matter. with squirrelmail and i'm getting "ERROR: Connection dropped by IMAP server." and with Thunderbird it tells me that it can't connect, neither imap nor sending with smtp are working.
tried telnet to port 25 from my computer and it times out, telnet from server to localhost on 25 works fine, and i sent an email to my server provider and they said 25 wasn't blocked and they could telnet to it successfully as well.
so somewhere i dun goofed...

config for postfix:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name 
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = hivemind.dyndns-server.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = hivemind.dyndns-server.com, localhost.hivemind.dyndns-server.com, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 5368709120
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-dovecot-postfix.conf -n -m "${EXTENSION}"
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sender_restrictions = reject_unknown_sender_domain
smtp_use_tls = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium

```

since the conf file for dovecot has a mariad of comments, i'll just put the uncommented lines:
```
listen = *
log_timestamp = "%Y-%m-%d %H:%M:%S "
ssl_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
ssl_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
login_greeting = Dovecot ready.
mail_location = mailbox:~/Mail/
imap_client_workarounds = tb-extra-mailbox-sep
pop3_uidl_format = %08Xu%08Xv

```

please lay down some ideas, even if said ideas are going on the assumption that i'm a tool :-D been using ubuntu for a couple years on home computers, never tried a mail server though, until i got this server.

---

### Post by truthseer0 on 2010-11-12
can nobody help me :(?

---

### Post by junapp on 2010-11-13
no help here, but illustrates why I moved everything to google apps for domains. Let them host it, it gets synced up and integrated into all the new phones and devices, gets fixed before you know there is a problem, and plenty of storage.

---

### Post by dcstar on 2010-11-13
> **truthseer0 said:**
> 
..........
please lay down some ideas, even if said ideas are going on the assumption that i'm a tool :-D been using ubuntu for a couple years on home computers, never tried a mail server though, until i got this server.

So **you** have port 25 on your server available to the outside world on a direct public IP address, or **you **have set up port translation on your network equipment and tested that it works?

---

### Post by Jumpmasterrt on 2010-11-14
At least you got further than I did.... I can't even get telnet to connect to check it...

I followed the Server Guide exactly but I got nothing from the get go....

All I want is for people to be able to SEND me mail from my website. It shouldn't be to hard to do that right?

---

