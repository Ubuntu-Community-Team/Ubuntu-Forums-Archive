---
title: "router not auto setting dhcp settings, can't connect"
date: 2011-08-02
forum: General Help
---

### Post by yobird42 on 2011-08-02
I installed 11.04 today, it connected fine off the live cd but no luck once I booted into the new os. 
When I click on my network, it tries to connect for a minute or so then stops. I tried running dhclient and nothing happened. I tried editing /etc/network/interfaces and that didn't work. 
So finally I decided to setup a static ip. I set the address to 192.168.0.1.155, the netmask to 255.255.255.0 and the router address 192.168.0.1. I thought that worked until I realized I could only connect to my router config page and nothing else.

here's the hardware I'm using:

Atheros AR9285 wireless adapter
Dlink gamer lounge DGL-4300

---

### Post by dcstar on 2011-08-03
> **yobird42 said:**
> I installed 11.04 today, it connected fine off the live cd but no luck once I booted into the new os. 
When I click on my network, it tries to connect for a minute or so then stops. I tried running dhclient and nothing happened. I tried editing /etc/network/interfaces and that didn't work. 
So finally I decided to setup a static ip. I set the address to 192.168.0.1.155, the netmask to 255.255.255.0 and the router address 192.168.0.1. I thought that worked until I realized I could only connect to my router config page and nothing else.


Use the Network Manager and set the DNS entry to 192.168.0.1.

---

