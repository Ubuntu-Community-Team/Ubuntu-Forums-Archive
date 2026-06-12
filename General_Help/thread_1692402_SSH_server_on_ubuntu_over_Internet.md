---
title: "SSH server on ubuntu over Internet"
date: 2011-02-21
forum: General Help
---

### Post by gtirtha on 2011-02-21
Hi Geeks,

I have install ssh server on my ubuntu machine and my machine is connected to Internet using 3G modem.

I want to access this machine over Internet and I want a ssh access only (no GUI, so no VNC or remote desktop stuff).

What could be possible solution on Ubuntu. Is there any application that can host SSH server with DHCP IP??

Note: I have heard about no-ip thing. How's that?? Will it map my DHCP IP each time my machine boots up??? Or after each boot up I have do some config manually to make it up???

Waiting for your expert suggestion.

---

### Post by Habitual on 2011-02-21
[http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html](http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html)

Yes, if using no-ip.com for Dynamcic DNS then
ssh myserver.no-ip.com will work.

---

### Post by gtirtha on 2011-02-21
Thanks a lot Habitual.

So, is this one time configuration or does it needs to be reconfigured each time after rebooting the system??

---

