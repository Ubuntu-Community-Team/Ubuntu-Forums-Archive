---
title: "Firewall (ufw) blocking everything."
date: 2011-05-02
forum: General Help
---

### Post by forestG on 2011-05-02
Hi! I am using ufw and gufw to configure my firewall. So I have the incoming in deny status and outgoing in "allow"  with the following rules applied:

To                         Action      From
--                         ------      ----
21/tcp                     ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere
135,139,445/tcp            ALLOW       Anywhere
137,138/udp                ALLOW       Anywhere
25/tcp                     ALLOW       Anywhere
22                         ALLOW       Anywhere
5900/tcp                   ALLOW       Anywhere
631/tcp                    ALLOW       Anywhere
68/udp                     ALLOW       Anywhere


My main problems are that when firewall is on, https is not responding  for some pages and network printers cannot be accessed either. Both problems did not exist in 10.04 and 10.10. When I shutdown the firewall there is no problem at all.

---

### Post by forestG on 2011-05-03
I think i solved it by myshelf. I was adding the service rule but this end up at adding the port 631 for the TCP protocol only. I put it both protocols and it worked fine.

---

