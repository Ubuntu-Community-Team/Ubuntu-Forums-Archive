---
title: "Postfix Relay Access Denied"
date: 2010-06-03
forum: General Help
---

### Post by tdcrenshaw on 2010-06-03
When attempting to check my postfix install by using telnet to send an email to an address outside my local network, I get a relay access denied error.

This is how I attempted to send an email

```
telnet my_server 25
helo my_server
mail from: me@my_server
rcpt to: me@gmail.com
```

and I get this

```
554 5.7.1 <me@gmail.com>: Relay access denied
```

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

myhostname = my_server
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = my_server, my_computername, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 my_server
relay_domains = my_server
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
home_mailbox = Maildir/
mailbox_command =
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

I've tried a bunch of different stuff to no avail. The only thing that appeared to work was adding gmail.com to relay_domains, but the email never appeared in my inbox.

If it helps, I'm using comcast as my isp; I've heard they block port 25, but I'm not sure how to change that configuration.

Thanks in advance

---

### Post by daamaya1982 on 2010-06-03
Why don't you try to authenticate when sending? You're not running an open relay SMTP server.

```

telnet myserver.com 25
helo myserver.com
AUTH LOGIN "your login converted to base64"
"your password converted to base64"
mail from:<me@myserver.com>
rcpt to:<user@outside.com>
data
Subject: test
I am testing this
.
quit

```

Comcast cannot block you from connecting to localhost on port 25. They can block other users on the internet from connecting to your host on port 25 though.

---

### Post by tdcrenshaw on 2010-06-03
How do I convert my username and password to base64?

---

### Post by daamaya1982 on 2010-06-03
Wow...

[http://tinyurl.com/29mcfm6](http://tinyurl.com/29mcfm6)

First link on results page.

---

### Post by dcstar on 2010-06-03
> **tdcrenshaw said:**
> When attempting to check my postfix install by using telnet to send an email to an address outside my local network, I get a relay access denied error.

This is how I attempted to send an email

```
telnet my_server 25
helo my_server
mail from: me@my_server
rcpt to: me@gmail.com
```

and I get this

```
554 5.7.1 <me@gmail.com>: Relay access denied
```

```

.........
myhostname = my_server
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
**mydestination = my_server, my_computername, localhost.localdomain, localhost**
relayhost =
**mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 my_server**
relay_domains = my_server
.........

```

I've tried a bunch of different stuff to no avail. The only thing that appeared to work was adding gmail.com to relay_domains, but the email never appeared in my inbox.

If it helps, I'm using comcast as my isp; I've heard they block port 25, but I'm not sure how to change that configuration.

Thanks in advance

You **cannot** connect to your server from an IP address not in the mynetworks list and send e-mail to destinations not inside your server (mydestination) - that would make your server an open relay.

You can send to destinations inside your server, and if you connected from inside your server you can then send to destinations outside your server.

Postfix is doing exactly what it is supposed to do.

---

### Post by daamaya1982 on 2010-06-03
> **dcstar said:**
> You **cannot** connect to your server from an IP address not in the mynetworks list and send e-mail to destinations not inside your server (mydestination) - that would make your server an open relay.

You can send to destinations inside your server, and if you connected from inside your server you can then send to destinations outside your server.

Postfix is doing exactly what it is supposed to do.

Correct, somewhat. If you authenticate then you do not have to worry about the open relay aspect of SMTP, and you will then be able to send. So... authenticate to the server and then send.

---

### Post by tdcrenshaw on 2010-06-03
> **daamaya1982 said:**
> Wow...

[http://tinyurl.com/29mcfm6](http://tinyurl.com/29mcfm6)

First link on results page.

I deserve that lol. I'll check to see if that works after I get back from dinner

---

### Post by dcstar on 2010-06-03
> **daamaya1982 said:**
> Correct, somewhat. If you authenticate then you do not have to worry about the open relay aspect of SMTP, and you will then be able to send. So... authenticate to the server and then send.

But why should authentication be necessary, the OP has not mentioned that it is a requirement only that a "test" of sending mail failed.

If the OP was simply telneting into the server from an IP on his internal network then it will fail, because there is no internal network range in the allowed addresses.

---

### Post by daamaya1982 on 2010-06-03
I am an administrator for 4 Qmail servers, and 2 Postfix servers. When testing, we always use telnet and we authenticate because our servers require authentication. Why? They are not open relay, and you must be an authenticated user in order to use them. So, why would we not authenticate?

---

### Post by dcstar on 2010-06-03
> **daamaya1982 said:**
> I am an administrator for 4 Qmail servers, and 2 Postfix servers. When testing, we always use telnet and we authenticate because our servers require authentication. Why? They are not open relay, and you must be an authenticated user in order to use them. So, why would we not authenticate?

Because it is not necessary in a lot of situations, like when you don't need it for a simple network when you only need to use the SMTP server from inside that network.

If the OP needs to access his SMTP server from outside his network then fine, use authentication, but it is basically bogus to tell people to unnecessarily use more complicated methods for no good reason other that "I use them".

I have been setting up and administrating mail servers on various platforms for various decades now, there are situations that require individual setups and you don't impose unnecessary extra complications when you don't have to.

---

### Post by tdcrenshaw on 2010-06-03
When I authenticate, I no longer receive a relay access denied error message, but I do not receive the email.

---

