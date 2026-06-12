---
title: "squid + time restrictions on specific sites and pc"
date: 2011-07-24
forum: General Help
---

### Post by jduval on 2011-07-24
how to do this on squid?

this is the scenario:
192.168.0.1 -> ubuntu
192.168.0.2 -> my pc
192.168.0.x -> pc's connected on lan

squid is working fine, primary use is proxy+cache

this is what i want to achieve
block facebook.com from 8am - 12pm and 130pm to 5pm on ip 192.168.0.3-192.168.10.0.x

tia

---

### Post by jduval on 2011-07-24
this is what i have so far

acl banned_ip src 192.168.0.3/255.255.255.255-192.168.0.250/255.255.255.255
acl blocked_domains dstdomain .youtube.com .twitter.com .facebook.com
acl mornings time M T W H F 8:00-12:00
acl afternoons time M T W H F 13:30-17:00
http_access deny banned_ip blocked_domains mornings afternoons 


but its not working
what is wrong with it?

---

### Post by SeijiSensei on 2011-07-24
I think you can only AND two ACLs in a single line.  Try this:

```
http_access deny banned_ip blocked_domains mornings
http_access deny banned_ip blocked_domains afternoons 
```

---

### Post by blueridgedog on 2011-07-24
Here is an example doing what you are attempting:

[http://squid-web-proxy-cache.1019090.n4.nabble.com/blocking-domains-certain-times-of-day-td1037600.html](http://squid-web-proxy-cache.1019090.n4.nabble.com/blocking-domains-certain-times-of-day-td1037600.html)

---

