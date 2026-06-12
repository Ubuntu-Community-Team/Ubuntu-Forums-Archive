---
title: "Default network interface"
date: 2009-08-07
forum: General Help
---

### Post by dainiookas on 2009-08-07
Hi,
I've kind of a specific problem. I have 2 physical network interfaces and a loopback interface alias, which has a normal real address , not local one. The server is being reached throught this interface. The IP's on physical interfaces are used only for the server to communicate with 2 routers. I'm looking a way to mark all of the outgoing packet's source address like the one on the loopback inteface's alias.
I know RedHat has a feature like this ( [http://redhat.activeventure.com/8/referenceguide/s1-networkscripts-interfaces.html](http://redhat.activeventure.com/8/referenceguide/s1-networkscripts-interfaces.html) ) 
PEERDNS=<answer>, where <answer> is one of the following:

yes — Modify /etc/resolv.conf if the DNS directive is set. If you are using DCHP, then yes is the default.

no — Do not modify /etc/resolv.conf.

**SRCADDR=<address>, where <address> is the specified source IP address for outgoing packets.**

The question how can I possibly make something similar in ubuntu.

What I do know, is I use iptables SNAT to mark all the outgoing packets, but maybe there is a better way.

Thanks

---

