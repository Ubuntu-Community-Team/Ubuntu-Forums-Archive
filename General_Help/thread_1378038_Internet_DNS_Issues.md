---
title: "Internet DNS Issues"
date: 2010-01-10
forum: General Help
---

### Post by olevrec on 2010-01-10
I have been trying to connect to the internet with a wired LAN connection for a while now with no luck. Running version 8.04 LTS on a 32-bit desktop.

Interestingly, my 64-bit desktop running version 8.04 64-bit automatically connected to the internet with no problems or input from me. Both are connected to the same router.

I figured i'd try and copy the network manager settings from the 64-bit machine to the 32-bit machine, which involved setting an automatic configuration (DHCP}. All went well except no DNS server address showed up on the 32-bit system, despite there being one on the 64-bit system. Trying to run Firefox like this results in the 'page load error' page coming up immediately.

I then manually added the DNS server address from the 64-bit system to the 32-bit system, and all that did was prolong the time it takes for the 'page load error' page to appear.

Anyone have any idea what could be wrong here?
Thanks in advance.

---

### Post by dcstar on 2010-01-11
> **olevrec said:**
> I have been trying to connect to the internet with a wired LAN connection for a while now with no luck. Running version 8.04 LTS on a 32-bit desktop.

Interestingly, my 64-bit desktop running version 8.04 64-bit automatically connected to the internet with no problems or input from me. Both are connected to the same router.

I figured i'd try and copy the network manager settings from the 64-bit machine to the 32-bit machine, which involved setting an automatic configuration (DHCP}. All went well except no DNS server address showed up on the 32-bit system, despite there being one on the 64-bit system. Trying to run Firefox like this results in the 'page load error' page coming up immediately.

I then manually added the DNS server address from the 64-bit system to the 32-bit system, and all that did was prolong the time it takes for the 'page load error' page to appear.

Anyone have any idea what could be wrong here?
Thanks in advance.

Post the following from both systems:

```
ifconfig
netstat -rn
cat /etc/resolv.conf
cat /etc/network/interfaces
arp -a
```

---

