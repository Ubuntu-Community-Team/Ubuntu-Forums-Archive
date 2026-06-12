---
title: "Port Forwarding not working"
date: 2011-10-09
forum: General Help
---

### Post by Valpskott on 2011-10-09
So, I've got 4 machines on my network...

1, Main computer - Ubuntu 11.04
2, Laptop - Ubuntu 10.10
3, Server - Xubuntu Server 10.04
4, Server - Ubuntu Server 10.10

I've successfully set up port forwarding to computers 2,3 and 4. I can access my servers from other (non local) places and so can others. I've also tested the ports via a port-scanning website.

Prior to updating computer 1 from Ubuntu 10.10 to 11.04 the port forwarding also worked on that computer.

```
:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Doesn't seem like iptables is blocking anything. Yet, Transmission reports the port to be blocked even when the router has port forwarding activated to the port in Transmissions preferences. This (the port being blocked) is confirmed (as being blocked) by the port scanning site as well.

I've even got uPNP enabled both in Transmission and in the Router. But downloads just won't start.

Is there a known port issue with Ubuntu 11.04 or are there any other firewall than iptables that I don't know of?

Any suggestions would be apprechiated.

---

### Post by gordintoronto on 2011-10-09
I've used Transmission, and it never required port forwarding. How about including your router setup in a message?

---

