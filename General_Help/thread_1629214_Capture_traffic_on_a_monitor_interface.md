---
title: "Capture traffic on a monitor interface"
date: 2010-11-23
forum: General Help
---

### Post by sammydafish on 2010-11-23
I'm trying to figure out why I cant capture traffic on the network interface.  I'm using a netgear WG111v3 using a RTL9198B chipset.  I have the compat-wireless drivers with the frag patch.  I'm able to do an injection test on the interface and it works.  I am able to create a monitor interface using airmon-ng.  I don't know how to test if this interface is picking up traffic though.  I'm trying to use firesheep and get nothing when I start capture on mon0  If I use my other wireless I can get local traffic but nothing from other machines.  That interface is not running monitor mode though.  When I start capture on mon0 I don't get anything, not local or external traffic.

It took a few times to compile firesheep successfully so I'm not sure if this problem is due to the network interface or firesheep and I don't know how to test to tell the difference.  

thanks

---

