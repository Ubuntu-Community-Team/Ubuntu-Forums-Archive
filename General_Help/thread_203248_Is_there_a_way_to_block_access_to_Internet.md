---
title: "Is there a way to block access to Internet?"
date: 2006-06-24
forum: General Help
---

### Post by xp_newbie on 2006-06-24
For data security purposes, I would like to disengage from the Internet while connected to my "Windows shares" on the LAN (where my data resides).

I don't want to do this permanently but rather dynamically: when on the Internet, disconnect from the "Windows shares", and when connected to the "Windows shares" disconnect from the Internet.

What is the proper way of accomplishing this on Ubuntu?

Thanks,
Alex

---

### Post by Fass on 2006-06-24
I think what you want is doable with [Firestarter](http://www.fs-security.com/). I haven't tried it, though, so I don't really know how you'd accomplish it. I know it has a button for blocking Internet access quickly, but if that allows you to still access shares, I don't know. I does also have options to whitelist or blacklist traffic, which could do the trick.

---

### Post by adrianhensler on 2006-06-24
No definite answer here; just possible starting points:

While I leave the exact solution as an exercise for the reader; or for someone who knows the options for ifconfig better than I do - I would think you would just use the ifconfig command to make a netmask that only allows for your (I assume) non-routable LAN network - 192.168.x.x for example.

I don't to lead you astray; but I think this is what I would start looking at; maybe someone else has beeter ideas. You could likely accomplish the same result with most firewall software or iptables. Now that I mention it perhaps iptables would be the more logical place to start.

---

### Post by xp_newbie on 2006-06-25
Thank you both for your answers.

While using an external firewall package is a possible solution, I was trying to find a way that doesn't require installing it (iptables seems the best firewall but it may be an overkill for what I am trying to accomplish).

Also I prefer keeping the IP address fixed to simplify maintenance from other PCs on the LAN (all PCs on my LAN, including the Ubuntu one have addresses of 192.168.0.x).

I was thinking perhaps in the direction of modifying the **routing table** of this Ubuntu PC only. I know that it is possible to achieve a routing table that allows access to all computers in the LAN, but does blocks all traffic to the internt, but how do I accomplish that?

Thanks,
Alex

---

