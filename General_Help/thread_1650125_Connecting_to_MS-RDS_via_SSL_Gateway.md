---
title: "Connecting to MS-RDS via SSL Gateway"
date: 2010-12-21
forum: General Help
---

### Post by Bonez56 on 2010-12-21
Hi all,

I use Ubuntu 10.10 x64 at home. My company uses Microsoft RDS (remote desktop services, aka terminal services) at work and I'd like to know if it's possible to connect from home.

On a Windows machine, there is an extra tab in the remote desktop client that allows you to specify a secure gateway to connect through - this means you don't need to establish a VPN connection beforehand, it simply just connects straight away via an SSL tunnel.

I've looked at quite a few Ubuntu RDP clients and none of them seem to have this option.

Does anyone know if it can be done? Either that or I'd like to get my hands on a copy of the 64 bit linux Cisco VPN client that works. I've found a few copies around the internet but they always fail to install.

Thanks in advance.

---

### Post by Wtower on 2010-12-21
Hm interesting one. Maybe stunnel:

[http://manpages.ubuntu.com/manpages/lucid/man8/stunnel3.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/stunnel3.8.html)

can be of help, but I never needed or used something alike so far.

Regards

---

