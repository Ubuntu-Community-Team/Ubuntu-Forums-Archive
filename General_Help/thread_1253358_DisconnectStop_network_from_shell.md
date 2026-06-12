---
title: "Disconnect/Stop network from shell"
date: 2009-08-30
forum: General Help
---

### Post by bgcommon on 2009-08-30
Hi ,
I am using Jaunty with kernel 2.6.30. I usually connect using a wireless connection. When connected I can see an option in NetworkManager applet to enable/disable the connection. 
1. I'd like to know if there is a similar provision from the shell.
2. I tried using '/etc/init.d/network stop' but even though the console output says that it has deconfigured the network interfaces, my internet connection ( via wireless ) works perfectly file. Can someone help me answer how that is?

---

### Post by nhanquy on 2009-08-30
what happens to **sudo ifconfig <interface> down/up **?

---

### Post by bgcommon on 2009-08-30
> **nhanquy said:**
> what happens to **sudo ifconfig <interface> down/up **?

That seems to work. When I did sudo ifconfig <interface> down , the network went down. But quickly ubuntu restored the connection automatically.

---

