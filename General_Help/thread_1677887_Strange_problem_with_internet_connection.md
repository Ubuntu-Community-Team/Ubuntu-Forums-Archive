---
title: "Strange problem with internet connection"
date: 2011-01-29
forum: General Help
---

### Post by vlad951 on 2011-01-29
Hello. I recently installed Kubuntu 10.10 on my machine, and I configured the PPTP VPN connection through which I connect to the internet.
I can successfully connect, but it works really slowly. Slower than it does on Windows 7 on the same computer, with the same settings for the PPTP dialer. In about 20 minutes after I connect, the connection fails and even the modem restarts itself. I tried setting the MTU for the pptp connection to 1400 (I checked, and 1372 is the maximum value before the packets start to fragment + 28 bytes for the IP/ICMP headers), but nothing seems to help.

---

### Post by vlad951 on 2011-01-29
bump

---

### Post by nukedeath on 2011-01-29
> **vlad951 said:**
> Hello. I recently installed Kubuntu 10.10 on my machine, and I configured the PPTP VPN connection through which I connect to the internet.
I can successfully connect, but it works really slowly. Slower than it does on Windows 7 on the same computer, with the same settings for the PPTP dialer. In about 20 minutes after I connect, the connection fails and even the modem restarts itself. I tried setting the MTU for the pptp connection to 1400 (I checked, and 1372 is the maximum value before the packets start to fragment + 28 bytes for the IP/ICMP headers), but nothing seems to help.

I am also having disconnect problems with PPTP VPN, but it happens in Windows also, so i think my problem is with my provider VyprVPN.

Have you tried getting on contact with your VPN provider, do you have the same problems in Windows?

---

### Post by vlad951 on 2011-01-29
> **nukedeath said:**
> I am also having disconnect problems with PPTP VPN, but it happens in Windows also, so i think my problem is with my provider VyprVPN.

Have you tried getting on contact with your VPN provider, do you have the same problems in Windows?

It works just fine in Windows, so I assume that it is a problem with the settings in Ubuntu.

---

