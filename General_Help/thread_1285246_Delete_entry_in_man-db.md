---
title: "Delete entry in man-db"
date: 2009-10-07
forum: General Help
---

### Post by falconindy on 2009-10-07
Is there a way to remove a reference in mandb to a page that should no longer exist? I had apt-get hang on me while it was processing man-db triggers. It removed the man page gzip but not the reference. I glanced through the man page for mandb, but I either missed or didn't see anything related to manually updating records in the db.

---

### Post by sedawk on 2009-10-08
I have no running Ubuntu machine here, so I can only give
hints towards the solution:
check the "-k" parameter in "man man", check
"man apropos" or "man whatis".

Depending on the flavour of Unix there are different
ways how it is done. I can remember "catman -w" and
/usr/sbin/makewhatis.
I'm not sure how to do it in Ubuntu, but there must
be a similar way to update the database.

---

