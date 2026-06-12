---
title: "Simple UFW question"
date: 2012-03-08
forum: General Help
---

### Post by mohrt on 2012-03-08
Hi,

I have a clean Ubuntu 11.10 Server x64 installation. I set my firewall up with a few simple ufw commands, similar to:

ufw default deny
ufw allow ssh
ufw allow www
ufw enable


Now, what is the proper way to save these settings so they are applied on reboot? I do not see an equivalent to "ufw save". I understand that ufw is a layer on top of iptables, so is the appropriate way to save the ufw settings by using iptables-save? If so, where would I save them so I know they will be loaded upon boot?

[edit] I think I understand this... ufw does not help with the save/restore of rules. So I saved the rules to /etc/iptables

> iptables-save > /etc/iptables

and I added the last line to /etc/network/interfaces on eth0:

> auto eth0
iface eth0 inet static
        address 10.0.0.2
        netmask 255.255.255.0
        gateway 10.0.0.1
        pre-up iptables-restore < /etc/iptables


Let me know if that is the way to do it, or there is a better way.

TIA

---

