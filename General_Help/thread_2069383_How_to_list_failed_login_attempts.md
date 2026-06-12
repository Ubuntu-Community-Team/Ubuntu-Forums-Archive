---
title: "How to list failed login attempts?"
date: 2012-10-10
forum: General Help
---

### Post by arcull on 2012-10-10
Hi guys,

I would like to know how to list failed login attempts on Ubuntu system (console and ssh). I've googled a bit and found out command ```
faillog
```, but it doesn't print the deliberately failed log in, don't know why. I remember on Suse I did grep the /var/log/messages to get the ssh failed logins. How do I it on ubuntu? Advices much appreciated, thanks.

---

### Post by Lars Noodén on 2012-10-10
Check in /var/log/auth.log, that's where the failed attempts should be recorded.

---

### Post by arcull on 2012-10-10
> Check in /var/log/auth.log, that's where the failed attempts should be recorded. very good, thanks :)

---

