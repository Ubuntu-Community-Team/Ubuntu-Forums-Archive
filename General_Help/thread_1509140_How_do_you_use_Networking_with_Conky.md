---
title: "How do you use Networking with Conky"
date: 2010-06-13
forum: General Help
---

### Post by Axilus on 2010-06-13
I currently have conky setup and working on my desktop and I recently tried setting it up on my laptop however the networking part of conky isn't working at all. The code I am using for it is:

```
${color 0096d1}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
```

My laptop connects via wireless to multiple locations. I have noticed that the address used is eth0 however I connect to multiple networks such as linksys, smith61, etc. Is there anyway to get it to work for multiple address?

---

### Post by Wardje on 2010-06-14
eth0 is for your wired internet connection, you'll most likely need to use wlan0 if you're on wireless.

In a terminal you can type ```
ifconfig
``` to see your different network interfaces.

---

### Post by Axilus on 2010-06-14
> **Wardje said:**
> eth0 is for your wired internet connection, you'll most likely need to use wlan0 if you're on wireless.

In a terminal you can type ```
ifconfig
``` to see your different network interfaces.

Thank you, changing all eth0's to wlan0 has worked.

---

