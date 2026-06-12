---
title: "Mail keeps bouncing for root@domain"
date: 2010-01-02
forum: General Help
---

### Post by StrangeWill on 2010-01-02
For some reason I think my system is generating messages for the user root@(domainname)

Not that it bothers me much, it seems to be two messages every 5 minutes, but it throw our statistics off, and I want to know why it's happening.

I can get Postfix to forward them to another address, but how can I just make them stop entirely?

Edit:
It's apparently from a CRON job that has this:
2>&1
Why is stderr mapped to mailing root@(domainname)?

---

### Post by falconindy on 2010-01-02
Fix the cron job. It's standard practice for cron jobs to send mail on error to the owner of the cron job. It's also usually good practice to have root **not** receive mail and, rather, have root's mail aliased to a real user.

---

