---
title: "mailx won't send mail"
date: 2009-10-13
forum: General Help
---

### Post by wbest on 2009-10-13
Hey mailx won't send out an email.
I keep getting:
/usr/lib/sendmail: Permission denied
As my error.

This is even when I use sudo.  I also tried chmod 666 to sendmail.  But still no go...

Any suggestions?

---

### Post by dyingsun on 2009-10-13
Does chmod 755 to sendmail do anything?

---

### Post by wbest on 2009-10-13
Nope...
chmod 755
and
chmod 777
both don't work

---

