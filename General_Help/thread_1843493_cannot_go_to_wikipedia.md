---
title: "cannot go to wikipedia"
date: 2011-09-13
forum: General Help
---

### Post by tiranuom on 2011-09-13
Guys,
I'm new to ubuntu. i cannot go to some sites like wikipedia from my ubuntu installation. i tried ping on it and it gives unknown host. but most of other sites are fine. 

please help me to resolve this.

by the way I'm using a broadband dongle to connect to internet.

---

### Post by zero2xiii on 2011-09-13
Hay,

I highly doubt this to be an ubuntu error.
But just for the sake of murphy's law, please post the output of
```
Sudo ifconfig
Sudo route
```

Just so we can make sure.

Is there anything non standard that you installed? Something like a firewall?

Cherz

---

### Post by mikewhatever on 2011-09-13
I think it's very unlikely that the problem has anything to do with Ubuntu. Perhaps this is a glitch with the DNS server. Try OpenDNS or GoogleDNS instead.

---

