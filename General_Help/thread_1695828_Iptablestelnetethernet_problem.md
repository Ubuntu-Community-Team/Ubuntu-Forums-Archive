---
title: "Iptables/telnet/ethernet problem"
date: 2011-02-26
forum: General Help
---

### Post by Defoe22 on 2011-02-26
Hi guys,

I've doing some uni work with iptables and wanted to know if I could 'hack' into another computer, connected to me by ethernet, by opening port 23 on the iptables?

Both computers are running Ubuntu 10.10 and are connected via ethernet. I am not sure whether it is a crossover cable - although internet is being shared by one to the other.

Just for the sake of getting to know iptables, telnet and other things better I would like to connect to one through telnet from the other.

I have set one computer to allow forward and output on port 23 (telnet) and specified the destination IP:

iptables -A FORWARD -p tcp -d 10.42.43.50 --dport 23 -j ACCEPT
iptables -A OUTPUT -p tcp -d 10.42.43.50 --dport 23 -j ACCEPT

and the other to accept INPUT from port 23 and the specified IP:

iptables -A INPUT -p tcp -s 192.168.2.2 --dport 23 -j ACCEPT

I then try to connect via telnet:
telnet
open 10.42.43.50 23
... and get connection refused or timed out messages

I'm taking computer security at uni and feeling pretty demoralised that I can't even hack a computer that I am wired to and have access to!

Am I going about this the right way? Any advice would be greatly appreciated...

---

### Post by Defoe22 on 2011-02-26
(bump)

---

