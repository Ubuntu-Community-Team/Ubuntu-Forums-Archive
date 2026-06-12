---
title: "Setting up squid ACL"
date: 2010-06-25
forum: General Help
---

### Post by karthick87 on 2010-06-25
I have the following ACL setup,


```
acl whitelist dstdomain "/etc/squid3/whitelist"
acl badURL url_regex "/etc/squid3/websites"
acl badURL url_regex "/etc/squid3/blockdownload"
acl badURL url_regex "/etc/squid3/blockedsites"
acl BROWSING time S M T W H F A 00:00-12:00
http_access allow whitelist
http_access deny badURL
http_access deny BROWSING
```

Websites in my whitelist is being accessed at any time,how to block whitelist between the time 00:00-12:00

---

### Post by kalistona on 2010-06-25
whitelist is allowed, blacklist not. 
how can you plan according time or agenda ? with rules.
is it in your firefox or ubuntu or from a special soft ?
I do not use this option so i am sure that someone else will help you soon.bye.

---

### Post by karthick87 on 2010-06-27
I am using squid in ubuntu,and planning to block my whitelist according to time.

---

