---
title: "Any whole Server Backup Management available?"
date: 2010-03-30
forum: General Help
---

### Post by ddtpoison on 2010-03-30
Hi,

While i am still running around Google and various forums in search of possible solutions, i would like to ask a question on this forum, in order to perhaps land upon a question quicker! :)

Years back i worked with a SysAdmin on SME using AFFA to handle whole server backups. I would like to know if there is a similar type of backup management for ubuntu servers, which anyone may know of?

Any form of assistance would be greatly appreciated! :D
Thank you.

---

### Post by HermanAB on 2010-03-30
Howdy,

Rsync is your friend.

There are several complicated scripts available that use rsync at the bottom of it all, but usually it is easiest to make your own, since it usually amounts to a one liner.

---

### Post by thebigob on 2010-03-30
Indeed rsync is the tool of choice however I would strongly recommend using rsnapshot.

This uses the rsync command however you can set up a config pop it in cron and forget about it.

I'm a bit of a Linux n00b and I managed it so anyone can :)

---

