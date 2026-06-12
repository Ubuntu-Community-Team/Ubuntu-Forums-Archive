---
title: "Determine Port Application Uses?"
date: 2012-03-24
forum: General Help
---

### Post by ShareBuntu on 2012-03-24
Hello,

I've got a Gmail notifier installed (gm-notify). However, I also have PeerGuardian installed which blocks all connections except those I specify. Gm-notify works fine when PeerGuadrian is turned off. So the question is, how do I find out what port gm-notify uses so that I may enable it in PeerGuardian like I did for port 80, 443, etc.

Thank you!

---

### Post by col48 on 2012-03-24
Internet search for 'linux  "what port" ' gives this link, which may be useful.

[http://www.cyberciti.biz/faq/find-out-which-service-listening-specific-port/](http://www.cyberciti.biz/faq/find-out-which-service-listening-specific-port/)

Looks like the command lsof in a Terminal (doesn't need sudo by the look of it) will tell you.  The difficult bit would be working out exactly what parameters you need and interpreting the output.

Lower down the same link, netstat.  Could be easier!  As long as gm-notify doesn't operate under a pseudonym, and as long as it always uses the same port.

Luck!

---

