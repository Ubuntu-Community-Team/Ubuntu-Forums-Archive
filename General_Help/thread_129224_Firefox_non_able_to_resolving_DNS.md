---
title: "Firefox non able to resolving DNS?"
date: 2006-02-13
forum: General Help
---

### Post by alzar on 2006-02-13
Hi 

I have the following problem with the 5.10 release of ubuntu. If I put the IP in the address line of firefox (for example 64.233.183.103 ) I do enter the site, if I put instead its DNS (for the previous example it is [www.google.com](www.google.com)) I do not enter the site.
It looks like my adsl router is not able to resolve the DNS.
On the other side if I run whois [www.google.com](www.google.com) or whois 64.233.183.103 this is working. In addition I am able to traceroute [www.google.com](www.google.com).
Has anybody any idea?

Alberto

---

### Post by taurus on 2006-02-13
Perhaps your /etc/resolv.conf is wrong then!!!  Look in there to make sure you have the nameserver for your router...

---

