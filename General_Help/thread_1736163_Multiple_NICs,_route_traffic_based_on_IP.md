---
title: "Multiple NICs, route traffic based on IP"
date: 2011-04-22
forum: General Help
---

### Post by PuckstopperGA on 2011-04-22
Hi,

Apologies in that I'm sure this has been discussed before, but my Google-fu is failing me at the moment.

I have an Ubuntu server box with multiple NICs. I'd like to specify that all traffic bound for a certain IP range goes through one NIC, and everything else goes through the other. Does anyone know how to do that? I'm not a total newbie, but I'm also not a linux guru (but usually can google my way to a solution...usually).

TIA!  :)

ETA: Source and destination IP for routing.
We have 1 NIC with a public IP, all public IP's should talk to it
Another NIC with a private IP, all private traffic should talk to this

In practice, I have some devices on a different subnet of the public IP range we have that will only talk to the private IP.

---

### Post by dino99 on 2011-04-22
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding)

most of the rules can be done inside the router i suppose, depending on your hardware config

[http://serverfault.com/questions/242830/how-to-route-all-traffic-to-one-host-trough-one-of-two-nics-on-linux](http://serverfault.com/questions/242830/how-to-route-all-traffic-to-one-host-trough-one-of-two-nics-on-linux)

[http://superuser.com/questions/9586/how-do-i-setup-ubuntu-linuxs-network-manager-to-selectively-route-network-traffi](http://superuser.com/questions/9586/how-do-i-setup-ubuntu-linuxs-network-manager-to-selectively-route-network-traffi)

---

### Post by IHeequ5i on 2011-04-22
Perhaps this will help:
[http://ubuntuforums.org/showthread.php?t=119787](http://ubuntuforums.org/showthread.php?t=119787)

---

