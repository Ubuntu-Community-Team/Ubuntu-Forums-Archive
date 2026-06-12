---
title: "/var/cache and /tmp, safe to delete?"
date: 2009-12-13
forum: General Help
---

### Post by User3k on 2009-12-13
Is it safe to delete (clean up the files inside) the /var/cache and /tmp folders? From what I understand the /tmp is already cleaned out anyways on reboot?

---

### Post by audiomick on 2009-12-13
Yes, I am pretty sure that tmp only hold it's contents for the current session.
As far as /var/cache goes, mine only has 50MB in it at the moment. It belongs to root, which is already a hint not to mess with it, and at that size, the saved space is nowhere near enough to risk breaking the system. I'd leave it alone.

---

