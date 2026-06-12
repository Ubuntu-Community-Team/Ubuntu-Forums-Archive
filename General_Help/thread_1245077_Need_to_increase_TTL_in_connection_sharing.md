---
title: "Need to increase TTL in connection sharing"
date: 2009-08-20
forum: General Help
---

### Post by Lockheed on 2009-08-20
I am using genome's network applet to share my eth0 internet on wlan0 ad-hoc network. 

Everything would be fine if my ISP didn't lower TTLs to 1 because now any computer behind my main home computer has no internet. How can in increase TTL in this specific situation?

---

### Post by Lockheed on 2009-08-20
This script solves the problem:
```
#!/bin/sh

iptables -F
iptables -F -t nat
iptables -F -t mangle
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -t mangle -A PREROUTING -j TTL --ttl-inc 128

echo "1" > /proc/sys/net/ipv4/ip_forward
```

---

