---
title: "Firestarter blocks ping?"
date: 2006-03-28
forum: General Help
---

### Post by worty on 2006-03-28
I'm having weird problems with Firestarter. It isn't allowing me to ping my local network but I can ping websites online. I'm using an edgeless network configuration with the two computers + ADSL modem all connected to a switch.

I get this message when I try to ping the other computer:
ping: sendmsg: Operation not permitted

I have figured out that it is firestarter that's blocking me but I can't figure out how to fix the problem without turning off the firewall.

Here's my iptables config in case it helps.
> Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  192.168.1.1          anywhere
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6881
ACCEPT     udp  --  anywhere             anywhere            udp dpt:6881
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6894
ACCEPT     udp  --  anywhere             anywhere            udp dpt:6894
LSI        all  --  anywhere             anywhere

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  ns.cybrnet.net       anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  ns.cybrnet.net       anywhere
ACCEPT     tcp  --  ns2.cybrnet.net      anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  ns2.cybrnet.net      anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  116-50-222-209.mycybernet.net  ns.cybrnet.net      tcp dpt:domain
ACCEPT     udp  --  116-50-222-209.mycybernet.net  ns.cybrnet.net      udp dpt:domain
ACCEPT     tcp  --  116-50-222-209.mycybernet.net  ns2.cybrnet.net     tcp dpt:domain
ACCEPT     udp  --  116-50-222-209.mycybernet.net  ns2.cybrnet.net     udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'


---

### Post by underwater on 2006-03-28
yeah I see several icmp echo dropped rules.  icmp echo is ping

---

### Post by seppo on 2006-03-28
You have a reference in your inbound chain to the LSI chain. In the LSI chain you drop icmp requests:

> 
DROP       icmp --  anywhere             anywhere            icmp echo-request
 
Get rid of it and ping request should get working again

---

### Post by worty on 2006-03-28
Thanks for the help. I did what you suggested but it didn't change anything.

Just to let you know, I can ping outside my internal network. It's just the internal network that it won't allow me to ping.

---

### Post by seppo on 2006-03-28
[quote=worty]Thanks for the help. I did what you suggested but it didn't change anything.

Just to let you know, I can ping outside my internal network. It's just the internal network that it won't allow me to ping.[/quote] 
What do you exactly mean with internal? Localhost? Or a host on the local subnet?

---

### Post by worty on 2006-03-28
Sorry I was unclear. I meant local subnet. I can't ping the other computer on my lan but can ping websites.

---

### Post by seppo on 2006-03-28
[quote=worty]Sorry I was unclear. I meant local subnet. I can't ping the other computer on my lan but can ping websites.[/quote] 
Well the problem isn't your linux host. The firewall makes no difference in outbound traffic to the local subnet or internet:

> 
Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere 
Do you have a firewall on the other machine running?

---

### Post by worty on 2006-03-29
I'm pretty sure that it is my localhost's firewall. When I turn it off, it works as it's supposed to.

Just to widen the problem, I've realized that it's not just ping. It's any connection to a local IP on the LAN that doesn't work.

---

