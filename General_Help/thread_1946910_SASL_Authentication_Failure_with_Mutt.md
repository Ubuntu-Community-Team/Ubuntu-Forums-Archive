---
title: "SASL Authentication Failure with Mutt"
date: 2012-03-25
forum: General Help
---

### Post by Earsplit on 2012-03-25
I've had zero problems with my regular @gmail.com address with Mutt.  This @bucknell.edu address however, will not let me send mail.  I get a "SASL Authentication Failure" every time I try.  Any ideas?  Are my servers set up properly?

The @bucknell.edu address is a google address, only with a different domain name.  This login info works for all other clients I've set it up with.  I'd really love to get mutt working.

Thanks guys!


Here's a snippet from my config, with the password and username changed out.

```
# IMAP
set from         = "USERNAME@bucknell.edu"
set imap_user         = "USERNAME@bucknell.edu"
set imap_pass         = "PWORD"
set folder         = "imaps://imap.gmail.com:993"
set imap_check_subscribed

# SMTP
set smtp_url        = "smtp://USERNAME@smtp.gmail.&#8203;&#8203;com:587/"
set smtp_pass        = "PWORD"

set spoolfile         = "+INBOX"
set postponed         = "+[Gmail]/Drafts"
set trash        = "imaps://imap.gmail.com/[&#8203;&#8203;Gmail]/Trash"

set header_cache         =~/.mutt/cache/headers
set message_cachedir         =~/.mutt/cache/bodies
set certificate_file         =~/.mutt/certificates
```


And here's a snippet from the debug output...

```
[2012-03-25 18:03:46] Looking up smtp.gmail.com...
[2012-03-25 18:03:46] Connecting to smtp.gmail.com...
[2012-03-25 18:03:46] Connected to smtp.gmail.com:587 on fd=6
[2012-03-25 18:03:46] 6< 220 mx.google.com ESMTP hr2sm26597687qab.8
[2012-03-25 18:03:46] 6> EHLO xubuntu-SXPS
[2012-03-25 18:03:46] 6< 250-mx.google.com at your service, [134.82.127.123]
[2012-03-25 18:03:46] 6< 250-SIZE 35882577
[2012-03-25 18:03:46] 6< 250-8BITMIME
[2012-03-25 18:03:46] 6< 250-STARTTLS
[2012-03-25 18:03:46] 6< 250 ENHANCEDSTATUSCODES
[2012-03-25 18:03:46] 6> STARTTLS
[2012-03-25 18:03:46] 6< 220 2.0.0 Ready to start TLS
[2012-03-25 18:03:46] SSL/TLS connection using TLS1.0 (RSA/ARCFOUR-128/SHA1)
[2012-03-25 18:03:47] 6> EHLO xubuntu-SXPS
[2012-03-25 18:03:47] 6< 250-mx.google.com at your service, [134.82.127.123]
[2012-03-25 18:03:47] 6< 250-SIZE 35882577
[2012-03-25 18:03:47] 6< 250-8BITMIME
[2012-03-25 18:03:47] 6< 250-AUTH LOGIN PLAIN XOAUTH
[2012-03-25 18:03:47] 6< 250 ENHANCEDSTATUSCODES
[2012-03-25 18:03:47] SASL local ip: 134.82.127.123;36547, remote ip:173.194.68.108;587
[2012-03-25 18:03:47] External SSF: 128
[2012-03-25 18:03:47] External authentication name: USERNAME
[2012-03-25 18:03:47] Authenticating (LOGIN)...
[2012-03-25 18:03:47] 6> AUTH LOGIN
[2012-03-25 18:03:47] 6< 334 VXNlcm5hbWU6
[2012-03-25 18:03:47] mutt_sasl_cb_authname: getting authname for smtp.gmail.com:587
[2012-03-25 18:03:47] mutt_sasl_cb_pass: getting password for USERNAME@smtp.gmail.com:587
[2012-03-25 18:03:47] 6> *****
[2012-03-25 18:03:47] 6< *****
[2012-03-25 18:03:47] 6> *****
[2012-03-25 18:03:48] 6< 535-5.7.1 Username and Password not accepted. Learn more at
[2012-03-25 18:03:48] SASL authentication failed
[2012-03-25 18:03:50] Postpone this message? ([yes]/no): 
[2012-03-25 18:03:51] mutt_free_body: unlinking /tmp/mutt-xubuntu-SXPS-1000-&#8203;&#8203;6696-8039055121269571200.
[2012-03-25 18:03:51] Mail not sent.
[2012-03-25 18:03:51] 4> a0021 NOOP
[2012-03-25 18:03:51] 4 a0022 CLOSE
a0023 LOGOUT
[2012-03-25 18:03:52] 4< a0022 OK Returned to authenticated state. (Success)
[2012-03-25 18:03:52] 4< * BYE LOGOUT Requested
[2012-03-25 18:03:52] Handling BYE
[2012-03-25 18:03:52] 4< a0023 OK 73 good day (Success)
[2012-03-25 18:03:52] IMAP queue drained
```

---

### Post by Earsplit on 2012-03-25
I figured it out...

For anyone else encountering this problem, I changed the line

```
set smtp_url        = "smtp://USERNAME@smtp.gmail.&#8203;&#8203;&#8203;com:587/"

```

to

```
set smtp_url        = "smtps://USERNAME@DOMAIN.EDU@smtp.gmail.&#8203;&#8203;&#8203;com:465/"
```

I had to change the port to 465, and use the secure smtp (smtps) to get this working.

Also make sure the packages gnutls-bin, openssl, and libsasl2 are installed.

---

