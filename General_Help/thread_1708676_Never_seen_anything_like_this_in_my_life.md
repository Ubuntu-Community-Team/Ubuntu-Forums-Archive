---
title: "Never seen anything like this in my life"
date: 2011-03-17
forum: General Help
---

### Post by nkae100 on 2011-03-17
... so I've forwarded incoming connections on port 25 to my virtual machine with the following commands:

> sudo iptables -t nat -A PREROUTING -p tcp -i eth0 -d 10.1.1.3 --dport 25 -j DNAT --to 192.168.56.101:25

sudo iptables -A FORWARD -p tcp -i eth0 -d 192.168.56.101 --dport 25 -j ACCEPT

The strange thing is the connections coming through in the virtual machine seem to be getting dropped. A port scan from the internet says the port is closed, but it is not the case as I can see the connection coming through.
As you've probably worked out, I am running a mail server. When I send myself test mail, the connections from the senders mail server also gets dropped.

Anyone ever had this experience before or has a clue whats going on?

---

### Post by Ocxic on 2011-03-17
change "iptables -A FORWARD -p tcp -i eth0 -d 192.168.56.101 --dport 25 -j ACCEP"
to
"iptables -A FORWARD -i eth0 -p tcp --dport 25 -j ACCEPT"

The incoming connection is not destined for your mail server it's destination is your computer/router/firewall since you're using a NAT setup.
The outside world does not see any computers behind your firewall, they just see your firewall. which is why you need to forward the connection in the NAT table.

secondly the main table is processed before the NAT table so iptables doesn't even realize the connection is being forwarded and drops it.

---

