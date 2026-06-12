---
title: "Stupid Firestarter Question."
date: 2010-02-16
forum: General Help
---

### Post by Vince N on 2010-02-16
I'm setting up a new router on my home network.  My plan is to have this routers firewall manage all network connections while also providing an additional layer of security from the IPTABLES firewall in Ubuntu.

However I also want to make sure than any traffic that's running on my local network from machine to machine be givin a free pass so that setting up things like Remote SSH inside the network, file and print sharing, etc are painless.  This includes wireless access as I am relying on WPA-PSK with MAC Filtering and a hidden SSID to keep my wireless network safe.  I assume this is adequately good to keep most casual snoopers out.

Am I correct in assuming that by setting my inbound connections to allow all traffic from 192.168.0.1/24 and setting outbound connections as permissive by default on each connected machine that this will basicly cause the firewalls on the computers to allow all traffic to each other but give greater scrutiny from data coming from the internet?

Any help or additional information would be appreciated.

As of right now the machines on the network are Ubuntu 9.04 and 9.10.  I will be adding a few more 9.10 based machines and upgrading 9.04 in the future but I assume the mixed versions won't cause too much of an issue with this.

---

### Post by Vince N on 2010-02-16
Bump

---

### Post by Dies on 2010-02-17
> **Vince N said:**
> ...
Am I correct in assuming that by setting my inbound connections to allow all traffic from 192.168.0.1/24 and setting outbound connections as permissive by default on each connected machine that this will basicly cause the firewalls on the computers to allow all traffic to each other but give greater scrutiny from data coming from the internet?
...

As long as all other incoming connections are set to DROP, sure.

 :)

---

