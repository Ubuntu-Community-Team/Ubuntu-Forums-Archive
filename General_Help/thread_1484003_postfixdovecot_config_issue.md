---
title: "postfix/dovecot config issue"
date: 2010-05-15
forum: General Help
---

### Post by eppo on 2010-05-15
the mail server itself will receive mail, that part works. i'm using dovecot imap to grab my mail, that works. but if i try to send mail from my iphone using an account on that server it doesnt work.
this is what i see in syslog:
May 15 07:14:52 coax postfix/smtpd[1432]: NOQUEUE: reject: RCPT from mobile-166-137-139-003.mycingular.net[166.137.139.3]: 450 4.1.8 <eppo@customconnexions.com>: Sender address rejected: Domain not found; from=<eppo@customconnexions.com> to=<xxxxxxx@aol.com> proto=ESMTP helo=<[10.25.15.47]>

i'm guessing this has somethign to do with the mydomains setting or the mynetworks setting?
any ideas?

---

### Post by eppo on 2010-05-15
had to do with dns issues. figured it out.

---

