---
title: "Unable to get a network connection"
date: 2010-06-21
forum: General Help
---

### Post by sr_guy on 2010-06-21
My Ubuntu Intrepid  8.10 box will not get a network connection. It's an older machine with 784Meg RAM and a semptron CPU. My other Ubuntu box is running 10.04 and gets a network connection fine, in fact all PC's and other networking devices get a connection except my Intrepid box.

I've tried:

1. Swap CAT5 cables
2. Change NIC cards.
3. Booted from a Live Ubuntu CD and still get an IP

My router is setup for DHCP and is setup for 50 leases. I'm at a loss

---

### Post by MooPi on 2010-06-21
Try this to see what might be the problem, in terminal: ```
ifconfig eth0
```To just try to get your adapter working try: ```
ifup eth0
```

---

### Post by sr_guy on 2010-06-21
neither worked. When I bootup I can see ubuntu go out and try to grab dhcp, and then says disconnected. I have CAT5 wired in my condo, so to rule out a wiring issue I connected a 2md router I have directly to that PC, and the same issue occurred, so I don't believe it's a wiring issue.

---

### Post by Iowan on 2010-06-21
What are results of **sudo dhclient eth0**?

---

### Post by sr_guy on 2010-06-21
It turned out to be a DHCP setup issue on my Asus WL-520GU router w/ DD-WRT installed

---

### Post by matt-fender on 2010-06-21
> **sr_guy said:**
> It turned out to be a DHCP setup issue on my Asus WL-520GU router w/ DD-WRT installed


I was just about to say, have you tried rebooting the router and double checking your router configuration lol

---

### Post by sr_guy on 2010-06-21
Yeah, when I set DHCP up I set up only for 5 DHCP leases for PC's that were not integrated on my network already (ie guests that are over), and 5 static leases. The mistake, I set the DHCP address to start on 192.168.1.2 which overlapped my static leases. Changed DHCP to start on 192.168.1.11, and all was happy

---

### Post by matt-fender on 2010-06-21
Glad it's sorted!, i've been battling with my netgear + skype issues... took me over a week to find out it's because of Netgears buggy firmware :lolflag:

---

