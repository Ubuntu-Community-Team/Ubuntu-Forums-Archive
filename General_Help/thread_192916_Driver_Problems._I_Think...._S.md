---
title: "Driver Problems. I Think.... :S"
date: 2006-06-09
forum: General Help
---

### Post by kane_666 on 2006-06-09
Well heres my setup: 2 Computers. 1 Server (Win XP) hosting dial-up which is connected to a wireless router via cable, and 1 client (Ubuntu) connecting to the server via wireless card and the router. The internet is shared via a proxy server installed on the server. Now the setup works, but the client losess internet on occasion... it justs drops out.

So far, i've tried a number of diffrent proxy servers which hasn't fixed the problem. I've re-installed the drivers, and ubuntu and same problem. So i've come to the conclusion that the problem is in the driver. The card is a DWL-G510 and the driver is RaLink's RA61STA.

So has annyone had this problem? or know of any way i can fix it.

Thanks!

---

### Post by dmizer on 2006-06-09
why are you using the ralink driver?  according to this page: [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards) your card works out of the box, so you shouldn't need a driver.

have you disabled ipv6?  if you have already disabled ipv6, then remove the driver and see if you can get your card to work without the ralink driver.

---

### Post by kane_666 on 2006-06-12
when i tried to run the card without any "3'rd party" drivers, the card wouldn't work so i found those drivers, tried it, and it worked. I didn't realise there were any native drivers... is there a link on how to use the card with those drivers?

---

### Post by dmizer on 2006-06-19
sorry about the delay in my reply.  i've been away on business.  if you've already gotten this to work by now, let us know what you did.  otherwise, read on:

there's lots of helpful information in the wiki for wireless.  i'm not familiar with this card exactly, but i'll do what i can to give you a hand.  if you unload (or just disable) the 3rd party drivers and boot the machine with the card in place, what does lspci say about your card?

also, check dmesg to see if your computer assigned a device (eth0, eth1, wlan0 etc) to your card.

do iwconfig and ifconfig and see if the card appears there.

also, tell me a bit about your setup.  are  you using wep for example?

---

