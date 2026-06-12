---
title: "retaining wireless connection"
date: 2006-06-07
forum: General Help
---

### Post by Ryanology on 2006-06-07
I was able to enable my wireless broadcom chip with fcuttter ( thank you thank you) and was just wondering if there is a way to have it ready on when the computer starts, currently I have to configure it manually on each restart. I have tried to save the session after  connecting to the net.

---

### Post by Ivan Matveich on 2006-06-08
Network interfaces are ultimately configured in your /etc/network/interfaces file. It should contain something like

```

auto wlan0
iface wlan0 inet dhcp

```

and "ifup wlan0" and "ifdown wlan0" will toggle the interface's active status.

If all that works, the interface should come up automatically...

---

