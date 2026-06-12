---
title: "problem setting up a router"
date: 2010-03-09
forum: General Help
---

### Post by satty8610 on 2010-03-09
All machines A, B and C discussed in this post are virtual machines(on vmware).

B and C are on separate networks.(B has ip add 172.16.208.130 and C has ip add 172.16.209.128. A had 2 network adapters with ip addresses 172.16.208.1 and 172.16.209.1. 
I "supposedly" set-up A as a Router between B and C , by running the command: 
```
on machine B:  ip route add default via 172.16.208.1 
```
```
on machine C:  ip route add default via 172.16.209.1
```

So, now B was able to ping C.

But what I cannot understand is that even when I shut down the "supposed-router" A , B is still able to ping C. How is that possible? If A is acting as a default gateway that forwards all packets from B to C, then shutting A down should stop B from being able to ping C.

Also, on doing [HTML]tcpdump -i eth0 at A[/HTML] , I am unable to catch any packets(this is while B is pinging C)

Please let me know whats the cause of this, and whether I have set up the router or not?

---

### Post by iponeverything on 2010-03-09
someone is listening to icmp redirects.

---

### Post by efflandt on 2010-03-09
Linux is smart enough to know about all local IPs.  So it can access any IPs on itself internally without any wire or routing, or will answer arp for any IP on itself.  If you specifically want to block or masquerade between interfaces, you may need to use iptables.

I once had 2 networks on one network with masquerade between an IP and alias IP on the same nic.  That was so I could connect the WAN of a router dumbed down to switch/AP to its LAN, and the Linux box would then masquerade that WAN IP as an IP on the LAN so it was within the LAN IP range of my internet router.  I did that so the dumbed down router could access public time servers for proper date/time in its logs.

So I had 2 networks on one LAN and Linux masqueraded one LAN as the other on one interface with 2 IPs.

---

