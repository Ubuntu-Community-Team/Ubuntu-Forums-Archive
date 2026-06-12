---
title: "does MUTT support SSL or TLS"
date: 2010-03-07
forum: General Help
---

### Post by e24ohm on 2010-03-07
I am trying to find a good text based email client for an older machine, which will not run the GUI correctly due to min. hardware; however, I want to be able to use it with Text based email clients.

Can anyone recommend a good text based email client that supports TLS/SSL for securied connections for IMAP, or even POP3?

Does MUTT support SSL/TLS?

Thanks.

---

### Post by oldos2er on 2010-03-07
Yes, mutt supports ssl.

---

### Post by andrew.46 on 2010-03-07
Hi Arrakis,

Test your own copy:

```

andrew@skamandros~$ mutt -v | grep -i 'ssl'
**[COLOR="Red"]+USE_SSL_OPENSSL[/COLOR]**  -USE_SSL_GNUTLS  -USE_SASL  -USE_GSS  +HAVE_GETADDRINFO

```

Andrew

---

