---
title: "AP Dynamic IP"
date: 2009-09-11
forum: General Help
---

### Post by InF3XioN on 2009-09-11
I have a TP-LINK 601G Access Point and I 'm trying to connect to my town 's Metropolitan Network. I have configured it to operate in Client Mode and I chose to get IP dynamically from network's DHCP server. But now I can't access the AP 's configuration menu, because the Gateway address changes every time I connect. Is there any way to do it without having to reset my AP 's configuration? I need a command to show me the AP 's dynamic IP.

---

### Post by P4man on 2009-09-11
IM not sure I completely understand what your doing (whats a metropolian network?) but your access point should have 2 IP addresses: a WAN (public) IP and a LAN (private) IP. The LAN IP is normally static, and something like 192.168.1.1 and you would find your web configuration page there. The WAN IP is typically dynamic and set by the provider using DHCP. You shouldn't need it to configure it, unless I am misunderstanding something.

---

### Post by InF3XioN on 2009-09-11
Well, I meant the LAN IP. Yes, it was normally static (192.168.1.1) and I used it to access AP's configuration page from there. But I changed it's option to "Dynamic" and now I need to find a way to access the configuration page without reseting the device. Thank you for replying.

PS. By "Metropolitan Network", I mean a public wide range wireless network that is used to provide free Internet access.

---

### Post by P4man on 2009-09-11
Ah, so you are connecting your AP to a wireless network?
In that case, good question. You could open a terminal and type

```
route
```

to find your default gateway (which should be your router)

---

