---
title: "Two Ip  Address, How to direct to two different folders on Apache?"
date: 2009-12-26
forum: General Help
---

### Post by Taurian on 2009-12-26
Is this possible?

I have two ip addresses.

Can I point one to var/www/folder1

and the other to

var/www/folder2

Can it be done without modifying the DNS on the Ubuntu Server?

Thanks!

---

### Post by bodhi.zazen on 2009-12-26
You do this in apache by defining virtual hosts.

DNS is different, you register with a DNS service and point the FQDN to the ip address.

[http://www.debianhelp.co.uk/virtualhosts.htm](http://www.debianhelp.co.uk/virtualhosts.htm)

---

