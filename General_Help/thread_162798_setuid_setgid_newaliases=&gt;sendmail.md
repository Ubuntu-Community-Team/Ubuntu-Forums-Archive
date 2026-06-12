---
title: "setuid setgid newaliases=&gt;sendmail"
date: 2006-04-19
forum: General Help
---

### Post by philosophia on 2006-04-19
hi i need for a regular user to be able to execute newaliases=>sendmail via suid/sgid 
is the right way to do this, as root = 'chmod 6777 newaliases'?
after i do that i notice that the permissions for newaliases has not changed, but the permissions for /usr/sbin/sendmail is rwsrwsrwx, and the user still can't execute it.

also - what permissions is /usr/sbin/sendmail supposed to have?  i probably screwed up its permissions.

---

