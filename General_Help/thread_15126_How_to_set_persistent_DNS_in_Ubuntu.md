---
title: "How to set persistent DNS in Ubuntu"
date: 2005-02-12
forum: General Help
---

### Post by jubuntus on 2005-02-12
Hi Ubuntumisers.
Here is the scenario.
PC Monica (Ubuntu 4.10 Warty) is a DHCP client. The gateway (Alcatel Speed Touch Pro) is a DHCP server on the private LAN side, and DHCP client on the WAN side. The gateway only does DNS forwarding, and this is sometimes flaky. DNS timeouts on Monica are common. The gateway/DHCP server cannot be configured to give out my ISP's DNS servers, it can only give itself and has to do DNS forwarding.
So my solution to this was to set the DNS servers manually on Monica. However, Monica forgets this DNS information upon reboot and following DHCP negotiation overwrites /etc/resolv.conf with the DNS info given by the gateway/DHCP server. Monica is, of course, still a DHCP client.
I think I can solve this problem (I'm not at her house anymore) by setting everything manually but I would like to know for future reference anyway, how to make the DNS servers you manually configure persistent across reboots, whilst still getting other IP goodies (address, mask, gateway, etc) from DHCP?
Actually, you don't even have to reboot for the network interface to forget your manually entered DNS servers, just restart the network service.

Computer->System Configuration->Networking->DNS tab. Should there not be an option something like Manually set DNS servers, or Get DNS servers from DHCP?

And one last thing, should there not be a Networking Section in the Software Support section?

---

