---
title: "After upgrading to 12.04, Postfix incoming email is all going deferred"
date: 2012-08-27
forum: General Help
---

### Post by supradave on 2012-08-27
Don't know what has happened, but after upgrading, email is going into the deferred queue by default.  postqueue -p shows the email and then I do a postsuper -H ALL to release them and then nothing happens.  I then restart postfix and the email gets delivered to dovecot.  I have MailScanner installed too.

Any ideas?

---

