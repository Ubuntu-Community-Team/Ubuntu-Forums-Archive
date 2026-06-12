---
title: "Problem Accessing Some Ports Remotely"
date: 2011-11-14
forum: General Help
---

### Post by mike.comeau on 2011-11-14
I have an Ubuntu Linux server running LAMP with ssh access and webmin. I can access everything fine from anywhere I want, even remotely, as I have all the proper ports forwarded to my router and a domain name attached to my home internet. The problem comes when I try to access ssh, scp, webmin, or any other port except (so far) ports 80, and 8080 at my school. I can access these ports from anywhere else, just not at my school. No, at my school I can only access the basic html pages on port 80. And I can also remotely administer my router from 8080. I go to QCC and it is the main campus in Worcester. Any ideas?

---

### Post by lolium on 2011-11-14
The most likely cause of this issue will be that those ports are being blocked by a firewall that QCC have implemented on their network. The only way around this would be to configure ssh to go over a different port but I do not recommend trying to get around Policies set in place by QCC as that could lead to you getting in trouble

---

