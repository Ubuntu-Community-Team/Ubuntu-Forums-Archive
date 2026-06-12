---
title: "Network Dropping Issue"
date: 2006-02-18
forum: General Help
---

### Post by dwessell on 2006-02-18
Hi all.. Here's an interesting one..

I have a D-Link DI614+ router..

One laptop hooked up to the network, running Kubuntu using a DWL 650+ NIC.

A PC using a standard onboard ethernet port.

When I boot the PC (Kubuntu), the laptop will begin to drop the connection every so often. With the PC off, the laptop functions fine.

Everything was working fine, until I installed Azereus (sp). I setup port forwarding on the router for TCP and UDP port xxxxx to go to the desktop PC. When the PC boots, it will have internet connection for a few moments, then it drops out. The Network Manager still shows a connection, but no domains can be found.

Needless to say Azereus has never worked :).

All of the network parts appear to be fine, as I dual booth with Windows on both machines, and everything functions fine there.

Any suggestions would be welcome.

Thanks
David

---

### Post by dwessell on 2006-02-18
All seems to be solved. I had setup the route to statically assign an IP to the desktop. That seems to reboot the network every 60 secs.. I went back to DHCP for the desktop, and all is well..

Thanks
David

---

