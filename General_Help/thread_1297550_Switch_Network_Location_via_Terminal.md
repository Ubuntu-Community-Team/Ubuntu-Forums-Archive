---
title: "Switch Network Location via Terminal"
date: 2009-10-21
forum: General Help
---

### Post by Unisyst on 2009-10-21
Hello,

I'm looking for a preexisting command to switch the network location (the gui option to switch between different networks, wireless, ppp(oe), etc) via the terminal. Currently using 9.04 Desktop.


I need to do it for scripting purposes.



Thanks in advance,
Uni

---

### Post by superdav42 on 2009-10-21
You probably are looking for ifup and ifdown```
ifup eth0
``` to start your ethernet connect and ifdown eth0 to stop it. Likewise ifup wlan0 will probably start your wireless. Of course your interface names will probably vary.

---

### Post by Unisyst on 2009-10-21
Hmmm not sure if that's quite what I want. Cause what I'm looking for is a way to easily switch between the profiles (one is DHCP, one is statically assigned IP, and one is PPPoE). I tried using pppoeconf but that actually broke the existing network manager (top left bar).

---

