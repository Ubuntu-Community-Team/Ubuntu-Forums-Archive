---
title: "iptables-restore failing"
date: 2010-05-02
forum: General Help
---

### Post by Blue_Jay on 2010-05-02
Hi,

I'm setting up a server with Jaunty Jackalope version. I'm trying to test setting up a basic iptables rules... No matter which command I put in, it is failing on the first command when I run iptables-restore < file location (the first rule always fails).  I'm doing this on the root user and first typing in the iptables rules in a test file.  I've tried the first command starting with % sudo, iptables and -A. All have the same result. I've also tried letting the HTTP rule be first with the same result.

Sample:
#All connections already established
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

#Allow HTTP and HTTPS
#$ sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT

I know there must be something obvious that I'm missing but can't figure it out... Any suggestions?

---

