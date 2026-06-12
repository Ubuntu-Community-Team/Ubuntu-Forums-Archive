---
title: "setting up postfix"
date: 2009-06-28
forum: General Help
---

### Post by wrathican on 2009-06-28
i have been following this guide on how to install and configure postfix 

[https://help.ubuntu.com/community/Postfix#Testing](https://help.ubuntu.com/community/Postfix#Testing)

when it comes to testing it says that i should see 250-starttls.
when i do ehlo localhost i get the following:
```

250-*SNIP* Hello localhost.localdomain [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
Connection closed by foreign host.
root@vps12:/etc/proftpd#

```

i guess it's to do with changine START=yes in /etc/default/saslauthd, which i have done, but to no avail.

is this setting neccessary? can i continue with my installation and setup with postfix working?

Thanks

Wrathican

---

