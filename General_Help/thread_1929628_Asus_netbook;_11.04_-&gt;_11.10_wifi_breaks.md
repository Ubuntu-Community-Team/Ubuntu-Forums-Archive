---
title: "Asus netbook; 11.04 -&gt; 11.10 wifi breaks"
date: 2012-02-22
forum: General Help
---

### Post by HonzaPokorny on 2012-02-22
ASUS Eee PC 1001PX

Upgrading to 11.10 from 11.04 breaks wifi. It's very flaky. Rebooting doesn't solve the problem. Can't reliably reproduce it.

---

### Post by HavarN on 2012-02-22
What wireless card are you using? Could you please post the outputs of these commands when run in a terminal:```
lspci -nn | grep Network
lsusb
```

---

### Post by HonzaPokorny on 2012-02-22
Thanks for your help, I wouldn't even know  where to start. Here's the debug information you asked for:

```

$ lspci -nn | grep Network
02:00.0 Network controller [0280]: Atheros Communications Inc. AR2427 Wireless Network Adapter (PCI-Express) [168c:002c] (rev 01)

$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13d3:5119 IMC Networks

```

---

