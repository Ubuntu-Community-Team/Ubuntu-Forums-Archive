---
title: "Prevent emailing errors?"
date: 2011-05-09
forum: General Help
---

### Post by ownaginatious on 2011-05-09
So recently I setup my system with exim4 so that it would be able to send any mdadm failures through a gmail address I set up for it to my email address.

Anyway, now pretty much every single application in the computer is trying to send mail using that gmail address to root@{domain name I made up}.com. Obviously, this is resulting in a ton of delivery failure notifications building up as that address doesn't exist.

Is there a way I can tell all these applications to just only drop their errors into logs rather than also trying to email 'root', while also retaining the ability for mdadm to email me?

Thanks.

---

