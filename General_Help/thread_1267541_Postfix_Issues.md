---
title: "Postfix Issues"
date: 2009-09-15
forum: General Help
---

### Post by pmcewan on 2009-09-15
I setup an email environment on Ubuntu using [http://flurdy.com/docs/postfix/edition5.html](http://flurdy.com/docs/postfix/edition5.html) and it works great.  However, I've implemented the recipient_bcc_maps which almost works except that it sends duplicate emails to people.  It appears that if they have an entry in aliases as well, that it duplicates email.  For example, if I had [email]somebody1@somewhere.com[/email] in aliases that mapped to [email]thisperson@somewhere.com[/email], but [email]thisperson@somewhere.com[/email] was in bccmaps as [email]anotherperson@somewhere.com[/email], then [email]anotherperson@somewhere.com[/email] receives 2 emails for every one sent to [email]thisperson@somewhere.com[/email].  Is there some way to fix this?  Thanks  -- Paul

---

