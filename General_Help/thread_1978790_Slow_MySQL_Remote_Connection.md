---
title: "Slow MySQL Remote Connection"
date: 2012-05-12
forum: General Help
---

### Post by Bros4Bros on 2012-05-12
I am running Ubuntu 10.04 as a web server (Rackspace host). I have cloned my server that is running MySQL locally. On the new server I changed the PHP code to connect to the original server through the internal ip address.

Pinging one server to the other through the internal ip address is less than 1 ms. So I basically have two identical servers - one is running MySQL locally and the other server is connecting to the other to run MySQL queries.

This is adding around 8 seconds to the page load time.

Original server (running MySQL locally):
[http://173.45.255.52/index.php?action=browse_members](http://173.45.255.52/index.php?action=browse_members)

Cloned server (running MySQL from original):
[http://bros4bros.com/index.php?action=browse_members](http://bros4bros.com/index.php?action=browse_members)

I have added "skip-name-resolve" to my.cnf, and this did not improve performance at all. Everything is up to date using "aptitude safe-upgrade".

I have a post on StackOverflow: [http://stackoverflow.com/questions/10558502/slow-mysql-remote-connection](http://stackoverflow.com/questions/10558502/slow-mysql-remote-connection)

The waterfall shows that it is just waiting for 8 seconds. I'm tearing my hair out trying to get this fixed. It's ridiculous that it's just sitting there for 8 seconds when the latency between the two server is less than 1 ms.

Cloned server waterfall:
[IMG]http://bros4bros.com/waiting.png[/IMG]

Live server waterfall:
[IMG]http://bros4bros.com/live_waiting.png[/IMG]

---

