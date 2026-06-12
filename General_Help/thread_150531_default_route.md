---
title: "default route"
date: 2006-03-26
forum: General Help
---

### Post by lupine_nickt on 2006-03-26
A bit of a niggling issue I've had for a while... I've got an ralink USB 802.11 network device, which I've been running with the rt2570 module. Just upgraded to dapper, and the module is seems to be included by default, which is most cool :)

Anyway, onto the problem: whenever I restart my computer, I lose my default route. I've got the command for it memorised by now - "route add default gw 88.96.18.246" - and since I restart my PC about once a week, it's easy enough to stick in each time I restart - but I'd love to get it running automatically.

So, the question: does anyone know how to get it to run that command at the same time as it brings my network interface up? I thought about adding it to /etc/network - maybe /etc/network/if-up.d/ - as a script, but I don't know if that's the best - or even right - way to set it up. 

Pointers, anyone? :)

xF,

...Nick

---

