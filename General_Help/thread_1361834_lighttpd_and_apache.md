---
title: "lighttpd and apache"
date: 2009-12-22
forum: General Help
---

### Post by nunyez on 2009-12-22
I installed a basic LAMP package some time ago and have since switched to lighttpd. I dont really need apache's features for any particular reason right now. I've removed, removed and purged, but to no avail each time my box restarts apache2 is running and lighttpd isn't. /etc/init.d/apache2 stop && /etc/init.d/lighttpd start fixes that but...

How to make lighttpd start by default instead?
- or - 
Is there a simple way to get apache to run on 81 instead? Last time I tried I failed miserably

---

### Post by bodhi.zazen on 2009-12-22
When removing apache, use the purge option. Then, if necessary, manually remove any residual boot scripts.

```
dpkg -l | grep apache
```

---

