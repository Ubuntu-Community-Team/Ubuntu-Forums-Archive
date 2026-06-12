---
title: "No window borders and no keyboard input"
date: 2011-05-03
forum: General Help
---

### Post by keraman on 2011-05-03
I installed Cisco AnyConnect Client on my Xubuntu 11.04 x64 machine.

Then I partially followed the instructions of [Cisco AnyConnect VPN Client on 64-Bit Ubuntu 10.04]("http://blog.mattwoodward.com/cisco-anyconnect-vpn-client-on-64-bit-ubuntu")

I created /usr/local/firefox then I followed step 5 and after a reboot of the machine I wasn't able to do any keyboard input nor did I see any window borders.

What have I done wrong and how can I fix that?

Thanks

---

### Post by dwmw2 on 2011-09-29
> **keraman said:**
> 
What have I done wrong and how can I fix that?


You installed the Cisco AnyConnect client. The fix is to remove it.

Ubuntu has a proper client for the AnyConnect VPN. It's called 'openconnect' and there is corresponding support for NetworkManager in the network-manager-openconnect package.

Just install those, and configure your VPN in NetworkManager.

---

