---
title: "Installing a replacement network card"
date: 2010-05-16
forum: General Help
---

### Post by maxpathan on 2010-05-16
I have a desktop PC running 8.04. Its been working fine without problems, however recently the onboard network stopped working. I installed a spare card and altered the BIOS to disable the onboard network adapter.

I reconnected the ethernet cable (which is attached to a d-link router). I now cannot connect to the internet.

One of the lights on the card does come on/off.
The router is fine because my laptop with 9.10 works fine over the internet.

What do i need to do for UBUNTU 8.04 to recognise the new card?

Thanks in advance

---

### Post by MartyBuntu on 2010-05-16
Does the new card show up in your Network Manager? eth1...eth0...

---

### Post by maxpathan on 2010-05-18
When I type ifconfig i see eth2, eth2:avahi and lo.

Is this what you are asking?

---

### Post by maxpathan on 2010-05-18
i entered ethtool -e eth2
i get:

driver: ne2k-pci
version 1.03
firmware-version:
bus info: 0000:00:0c.0

---

### Post by maxpathan on 2010-05-24
Hi
Can anyone provide any guidance?
Regards
Max

---

