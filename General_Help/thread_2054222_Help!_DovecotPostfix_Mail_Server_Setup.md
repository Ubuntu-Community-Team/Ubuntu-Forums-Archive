---
title: "Help! Dovecot/Postfix Mail Server Setup"
date: 2012-09-06
forum: General Help
---

### Post by Shadal on 2012-09-06
I've been fighting with Dovecot and Postfix for nearly 3 days now - I need some help!...

It seems Dovecot is not generating the private/auth file required for connections.

Mail.log
```

Sep  6 21:55:55 suncoastshores postfix/smtpd[11278]: warning: SASL: Connect to private/auth failed: No such file or directory
Sep  6 21:55:55 suncoastshores postfix/smtpd[11278]: fatal: no SASL authentication mechanisms
```

ls -l /var/spool/postfix/private/
```
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 amavis
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 anvil
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 bounce
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 bsmtp
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 defer
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 discard
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 dovecot
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 error
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 ifmail
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 lmtp
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 local
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 maildrop
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 mailman
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 proxymap
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 proxywrite
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 relay
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 retry
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 rewrite
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 scache
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 scalemail-backend
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 smtp
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 tlsmgr
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 trace
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 uucp
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 verify
srw-rw-rw- 1 postfix postfix 0 Sep  6 22:26 virtual
```

Hostname```
hostname
suncoastshores
hostname -f
suncoastshores.suncoastshores.com
```

Dovecot Main.cf (snippets)
```
# SASL parameters
# ---------------------------------
 
# Use Dovecot to authenticate.
smtpd_sasl_type = dovecot
# Referring to /var/spool/postfix/private/auth
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
smtpd_sasl_authenticated_header = yes


# General host and delivery info
# ----------------------------------
 
myhostname = suncoastshores.suncoastshores.com
myorigin = /etc/hostname
mydestination = suncoastshores.suncoastshores.com, localhost
```

10-master.conf (snippet)
```
  # Postfix smtp-auth
   unix_listener /var/spool/postfix/private/auth {
   mode = 0660
   user = postfix
   group = postfix
  }
```

What am I missing? Why won't Dovecot generate the private/auth file?

---

