---
title: "ping www.google.com, no reply"
date: 2010-03-18
forum: General Help
---

### Post by vksingh on 2010-03-18
Hi,

 I have install ubuntu 9.04 on my machine. When I am trying to ping google.com, I do not get ping reply but I am able to browse Internet. Also, I am able to ping any of the local machine on LAN. 

Please help,


Thanks,

Vivek

---

### Post by Grenage on 2010-03-18
Is your router blocking ICMP?

---

### Post by roccivic on 2010-03-18
Sounds like you are sitting behind a proxy or a firewall or a router...

---

### Post by CptPicard on 2010-03-18
Same here. I suspect Google simply doesn't respond to pings; can you imagine how many people would be pinging them if it worked in the first place? (Although their regular traffic is certainly something much more massive :) )

---

### Post by gnupipe on 2010-03-18
Try pinging rit.edu (for example) instead of google.

---

### Post by roccivic on 2010-03-18
> **CptPicard said:**
> Same here. I suspect Google simply doesn't respond to pings; can you imagine how many people would be pinging them if it worked in the first place? (Although their regular traffic is certainly something much more massive :) )

That's nonsense

```
roccivic@roccivic-pc:~/Desktop$ ping -c 3 google.com
PING google.com (xx.xxx.9.103) 56(84) bytes of data.
64 bytes from xx-xx-xxxx.1e100.net (xx.xxx.9.103): icmp_seq=1 ttl=55 time=24.0 ms
64 bytes from xx-xx-xxxx.1e100.net (xx.xxx.9.103): icmp_seq=2 ttl=55 time=22.7 ms
64 bytes from xx-xx-xxxx.1e100.net (xx.xxx.9.103): icmp_seq=3 ttl=55 time=23.0 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 22.726/23.275/24.054/0.579 ms

```

---

### Post by CptPicard on 2010-03-18
> **roccivic said:**
> That's nonsense


Perhaps, but at least factual in the sense that I'm not getting ping responses specifically from Google from where I'm sitting at :p

---

### Post by linden940 on 2010-03-18
what the hell u mean no one pings google?


pinging google is like doing a speed test....they are all ways online never off line so if u dont get nothing when u ping them...u have a problem....

---

### Post by Grenage on 2010-03-18
> if u dont get nothing when u ping them...u have a problem....

Or it simply means that a device (or possibly the ISP) is blocking ICMP ping.

---

### Post by linden940 on 2010-03-18
thats still on your side...but thats a point

i dont know of many isp who block that so if u have a router then unplug it and plug right into ur modem and see if you can ping and or go to the google website....if you still cant then maybe call up you ips or try another computer to see if you still can get on the web

---

### Post by Grenage on 2010-03-18
It's uncommon, but during some worm outbreaks, at least a few ISPs here (England) blocked ICMP traffic.  There OP is unlikely to have a terminal issue, because:

[QUOTE=vksingh]I am able to browse Internet. [/QUOTE]

They haven't posted back, so it's possible that rage got the better of them, and they chainsawed their computer in half.

---

### Post by linden940 on 2010-03-18
lmao.... well being able to browse Internet on the same network? or did they go to another network to make this post?

if they went to  dif network to make this post...idk why they will be posting here...i would be calling my isp..but i think you get what i mean

---

