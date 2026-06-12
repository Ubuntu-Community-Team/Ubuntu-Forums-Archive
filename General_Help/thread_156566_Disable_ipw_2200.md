---
title: "Disable ipw 2200"
date: 2006-04-07
forum: General Help
---

### Post by h3llfyr3 on 2006-04-07
Hi All,
I have an IPW220 which I want to disable (permenantly) As I use a pcmcia card instead.

Whilst I've disabled it in network-admin for some reason it still gets an IP address and associates itself with access points.....

On a similar note how can i restart networking on my pcmcia card as when using kismet it does'nt seem to drop out of rfmon mode properly and i htink i need to restart networking or something to get it working normally to associate with an AP.

EDIT
For anyone with the same issue
[http://www.thinkwiki.org/wiki/Ipw2200](http://www.thinkwiki.org/wiki/Ipw2200)
To enable power management, issue:

    # iwpriv wlan0 set_power 7 

where wlan0 is the name if your interface. This will reduce idle power consumption by several Watts compared to no power management.

    * To disable the radio (and further reduce power consumption) when the card is not in use, issue: 

    # echo 1 > /sys/bus/pci/drivers/ipw2200/*/rf_kill 

    * To enable the radio, issue: 

    # echo 0 > /sys/bus/pci/drivers/ipw2200/*/rf_kill 

    * To make the radio off by default after boot, add 

options ipw2200 disable=1

to your /etc/modprobe.conf or equivalent.

See README.ipw2200 in the ipw2200 package for details and other options.

---

