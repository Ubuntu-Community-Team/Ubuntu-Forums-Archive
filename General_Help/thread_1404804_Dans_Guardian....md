---
title: "Dans Guardian..."
date: 2010-02-11
forum: General Help
---

### Post by TechMansoor on 2010-02-11
My scenario is similar to this person scenario:
[http://www.howtoforge.com/forums/showthread.php?t=39855](http://www.howtoforge.com/forums/showthread.php?t=39855)

Here at the clinics, we already have established leaf/shorewall firewalls. Our domain controllers are win2k3 boxes.

I've installed ubuntu 9.10 on a sound desktop/server and installed two nics inside that box.

How do I make Dansguardian talk to our domain controllers, and give users access to the internet via established groups? What would be the best way to do this?

Thanks so much in advance guys!!!

---

### Post by t4thfavor on 2010-02-11
I think your looking for LDAP authentication for Squid, as dansguardian is just a content protection module for a squid proxy.

---

