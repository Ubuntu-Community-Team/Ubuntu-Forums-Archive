---
title: "login in to a machine on a separate subnetwork"
date: 2010-08-30
forum: General Help
---

### Post by meg23 on 2010-08-30
I have set up a dhcp server through a usb ethernet adapter to give IPs to a cluster starting at 10.0.0.10, however I am connected to eth0 as 192.168.2.215. I can see the dhcp lease given to the machines, starting at 10.0.0.10. How do I ssh into a machine on a different subnetwork? The IP of the machine I want to login to is 10.0.0.10. 

Thanks, Max

---

### Post by pricetech on 2010-08-30
I'm not entirely clear here, but I'll take a stab at it.

If you're talking about the machine you're connecting "from" handing out the DHCP leases, then it involves nothing more than using the IP given to the machine your are connecting to after making sure SSH is set up and working on the "to" machine.

If the machine you're connecting "from" is not the DHCP server, and is indeed on a separate subnet entirely, you'll need a route to that subnet through your gateway.

A little clarification might help.

---

### Post by meg23 on 2010-08-30
Thanks for your quick reply. Sorry for being short on details. 

I have a desktop with 2 ethernet cards, one that recieves an internet connection and has the IP of 192.168.2.215 and the other is DHCP server (10.0.0.1) that is attached to a bunch of embedded devices, starting at 10.0.0.10. My goal is to login to the embedded devices from the same desktop.  

It sounds like your second solution is what I need. How do I route that subnet through the gateway?

---

