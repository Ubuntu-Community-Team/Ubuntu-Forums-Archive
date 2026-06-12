---
title: "GDM keep LDAP user first login in the list"
date: 2010-12-07
forum: General Help
---

### Post by gnagnibu on 2010-12-07
Hi all, I write this post to solve an annoying problem: on my Ubuntu 10.04.1 GDM keeps tha list of LDAP users that login once into the system, including tty logins.
So, I can't find how to clear this list...

Fisrt, I've removed /var/lib/gdm/.cache/login_frequency.cache, then I've restarted GDM but it fails, so I think there is another process that keep login cache, like nscd...

Any ideas???

---

