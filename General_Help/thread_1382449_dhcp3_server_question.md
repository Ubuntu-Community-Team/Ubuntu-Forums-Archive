---
title: "dhcp3 server question"
date: 2010-01-16
forum: General Help
---

### Post by ripeart on 2010-01-16
Hello,

I originally posted this in the networking/wireless forum, however that may be the wrong forum as there have been no responses to it.

I have a mixed wired/wireless LAN. Ubuntu 9.1 Desktop is running off a G5 and I would like to use it as a DHCP server and eventually have it become a firewall and internet proxy.

Equipment:

Cable modem --> WRT54G --> Switch

The WRT54G is for wireless clients and the switch connects my wired clients (printers, network media server, etc.)

The problem I am facing is that I have wired and wireless clients that need to get their IPs from the server. The G5 is connected to the network via ethernet and I do not have a wireless adapter for it. Is there any way to circumvent using the Ubuntu box for DHCP? I can't think of any since the wireless clients need to get their IP info wirelessly.

Any thoughts would be appreciated.

Thanks!
[B]
edit1: Oh wait! Can my WRT54G be a DHCP client?!

[/B]edit2: Please tell me if this would work:

Cable modem --> [WAN IP] **WRT54G** [LAN IP 200.1.1.1] --> **G5** [IP 200.1.1.2] DHCP server --> [200.1.1.3 - 31]/27 - however in that configuration, how would the wireless clients get their IPs?

---

### Post by ripeart on 2010-01-16
Is there no one smart enough to help me figure this out? *sigh* :o

---

