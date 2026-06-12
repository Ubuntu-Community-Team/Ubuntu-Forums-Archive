---
title: "OpenVPN and DNS leaks"
date: 2012-02-08
forum: General Help
---

### Post by ericus on 2012-02-08
I'm all set with an OpenVPN anonymizing service, but the problem I have is when I run DNS leak tests on the internet (in example [https://www.dns-oarc.net/oarc/services/dnsentropy](https://www.dns-oarc.net/oarc/services/dnsentropy)) it shows bot my VPN providers DNS servers and also my *own* ISP's DNS, so that is a security issue. Any ideas on how to fix this on Ubuntu 10.04?

I am using the GUI network-manager to manage the OpenVPN-connection.

I've tried to install *nscd* and running ```
sudo /etc/init.d/nscd restart
``` after connecting, but without any progress. Sometimes that leaves me without working DNS servers at all after disconnecting.

Please help me out with this issue.
Thanks in advance.

---

