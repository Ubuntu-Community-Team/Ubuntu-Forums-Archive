---
title: "internet problems"
date: 2010-11-25
forum: General Help
---

### Post by techie1992 on 2010-11-25
hello,

i am new to ubuntu netbook remix. i have recently installed it on my emachines em250 netbook and my wireless is connected to my router but when i go to view a web page it says it cannot be found. i am unable to view web pages unless i am connected to my router via ethernet cable. its frustrating and i dont know how to solve it. please help me!!!!!1

---

### Post by Tobeus on 2010-11-27
I would start by pinging your router first.  Is your router giving you an IP address?

Right-Click on your network notification icon in the upper right of the screen and click Connection Information.  You should see your IP address in this screen, and a Default route.  The default route would be your router.

Open a terminal window under Apps>Accessories>Terminal and type:

```
ping [and the Default route IP]
```

Where you see [and the Default route IP] above, substitute your default route ip address, such as 192.168.1.1 or 10.0.0.254.  Press Ctrl+C to cancel the ping.

Do you receive a reply from the ping?

When I ping my default route, it looks like this:

> $ ping 192.168.16.50
PING 192.168.16.50 (192.168.16.50) 56(84) bytes of data.
64 bytes from 192.168.16.50: icmp_req=1 ttl=128 time=16.7 ms
64 bytes from 192.168.16.50: icmp_req=2 ttl=128 time=0.129 ms
64 bytes from 192.168.16.50: icmp_req=3 ttl=128 time=0.148 ms
64 bytes from 192.168.16.50: icmp_req=4 ttl=128 time=0.131 ms
^C
--- 192.168.16.50 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.129/4.287/16.742/7.190 ms


When I can't ping something, it looks like this:

> $ ping 192.168.16.250
PING 192.168.16.250 (192.168.16.250) 56(84) bytes of data.
From 192.168.16.30 icmp_seq=1 Destination Host Unreachable
From 192.168.16.30 icmp_seq=2 Destination Host Unreachable
From 192.168.16.30 icmp_seq=3 Destination Host Unreachable
From 192.168.16.30 icmp_seq=5 Destination Host Unreachable
From 192.168.16.30 icmp_seq=6 Destination Host Unreachable
From 192.168.16.30 icmp_seq=7 Destination Host Unreachable
^C
--- 192.168.16.250 ping statistics ---
7 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6007ms
pipe 3


Do you have a regular ip address (such as 192.168.x.x, or 10.0.x.x) or something different?

---

### Post by techie1992 on 2010-11-27
that solved it....thank you so much

---

