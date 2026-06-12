---
title: "No LAN access after upgrade to Karmic (ifupdown usb0)"
date: 2010-01-24
forum: General Help
---

### Post by PaulWhipp on 2010-01-24
I upgraded my dell mini from 9.04 to 9.10. Everything is fine and it works fine on wireless networks as before.

When I connect the LAN cable to the network port (not USB) it reports connected with "ifupdown (usb0)" but the network is unreachable (can't ping or browse).

In 9.04 it "just worked".

I found [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432777](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432777) and tried setting the managed=true as suggested but it did not work and warned me to set it back to false when I restarted networking.

The connection icon on the network manager shows two little plugs rather than the usual two monitors it used to show when it was working.

I don't often use the LAN connection but it is essential at times when no wireless is available in some offices.

Anyone any ideas?

---

### Post by PaulWhipp on 2010-01-28
I'm still stuck with this. 9.10 on my Dell Mini 9 is great until I go into an office that only has wired connections.

Networking works fine on wireless.

When I plug in the network cable, up pops "ifupdown(usb0)" in the network manager as a wired network and it reports that it is connected but ping and networking functions report that the network is unreachable.

In 9.04 before the upgrade I used to see eth0 not ifupdown(usb0) and everything worked fine.

I can't be alone... surely?

---

