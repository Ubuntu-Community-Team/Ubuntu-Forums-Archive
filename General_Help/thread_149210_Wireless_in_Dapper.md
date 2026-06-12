---
title: "Wireless in Dapper"
date: 2006-03-23
forum: General Help
---

### Post by bhilton on 2006-03-23
Dapper 6.04 seems to have correctly identified my wireless card as a Broadcom BCM4306 802.11b/g (Dell 1350 Mini-PCI Card).

If I go to System > Administration > Networking, it shows up as eth1.  If I set it up and choose activate, it hangs out for awhile and the status indicates that it was activated, but it won't work.  If I exit Network Settings and get back in again, it is as if I hadn't done anything previously.  The network card never shows up under Connection Properties.

I tried to edit /etc/network/interfaces to no avail.

I also tried to configure it with Ndiswrapper (which worked well for me in Breezy), but the card wouldn't show up in Network Settings with that either.  I think maybe because the card is already set up as eth1.

Is there a way to fix this?  If not, how do I remove my wireless card from eth1, so that I can maybe use ndiswrapper with the card on wlan0?

Thanks,

Brad

---

### Post by bhilton on 2006-03-23
Anybody?

---

### Post by int on 2006-03-23
Please use search link.
[http://ubuntuforums.org/showthread.php?t=149208](http://ubuntuforums.org/showthread.php?t=149208)

---

### Post by bhilton on 2006-03-23
Cool.  I followed the above link and now it works.  Thanks!

---

