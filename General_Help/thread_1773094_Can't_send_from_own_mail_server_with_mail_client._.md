---
title: "Can't send from own mail server with mail client. (Thunderbird or Evolution)."
date: 2011-06-01
forum: General Help
---

### Post by MrWestwood on 2011-06-01
This could be in the wrong section so my apologies in advance.

I have set up postfix and dovecot as per the Ubuntu anual and appear to have a functioning mail server.

Using the sendmail command I can send mail and I receive mail in ~/Maildir. Using Thunderbird I can read any mails received but I can't send any mail from Thunderbird. I have tried with both STARTTLS and SSL/TLS and whilst I get the prompt for a password I keep getting the message my password for my server is wrong.

I have ports 25, 465, 587 and 993. Is that all the right ports?

When I ping my domain name it resolves to my router name whereas I believe it should resolve to my IP. Could there be a problem with my host file? I've had a play but to no avail.

Here's the error in mail.log.
```

westwood@westwood-desktop:/etc$ tailf /var/log/mail.log
Jun  1 19:00:33 westwood-desktop postfix/smtpd[2376]: warning: localhost.localdomain[127.0.0.1]: SASL LOGIN authentication failed: generic failure
Jun  1 19:00:41 westwood-desktop postfix/smtpd[2376]: warning: SASL authentication failure: cannot connect to saslauthd server: Permission denied
Jun  1 19:00:41 westwood-desktop postfix/smtpd[2376]: warning: SASL authentication failure: Password verification failed
Jun  1 19:00:41 westwood-desktop postfix/smtpd[2376]: warning: localhost.localdomain[127.0.0.1]: SASL PLAIN authentication failed: generic failure
Jun  1 19:00:42 westwood-desktop postfix/smtpd[2376]: warning: SASL authentication failure: cannot connect to saslauthd server: Permission denied
Jun  1 19:00:42 westwood-desktop postfix/smtpd[2376]: warning: localhost.localdomain[127.0.0.1]: SASL LOGIN authentication failed: generic failure
Jun  1 19:00:48 westwood-desktop postfix/smtpd[2376]: disconnect from localhost.localdomain[127.0.0.1] 
```I really need your help guys. I'm almost there.

---

### Post by SeijiSensei on 2011-06-01
You need to fix this:

> SASL authentication failure: cannot connect to saslauthd server: Permission denied

---

### Post by MrWestwood on 2011-06-01
> **SeijiSensei said:**
> You need to fix this:

Have done and it's fixed.

Many thanks SeijiSensei.

Sometimes you just need that extra voice.

---

