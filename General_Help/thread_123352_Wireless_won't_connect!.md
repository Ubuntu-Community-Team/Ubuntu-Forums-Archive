---
title: "Wireless won't connect!"
date: 2006-01-29
forum: General Help
---

### Post by rudeboyskunk on 2006-01-29
So I'm running Breezy on my desktop, working great.  I decided to upgrade from Hoary on my laptop, but instead of just upgrading, I just did an overall install.

So anyway, I set everything up, and now the wireless doesn't connect.  I put the WEP key in correctly.  I typed in the name of the wireless broadcast.  Everything is configured right.  Should I have selected wifi0 instead of eth1?  It's a Cisco Aironet 350.  IBM Thinkpad T21, Pentium III.  Running GNOME.

---

### Post by Chris Tucker on 2006-01-30
if you have a network device called wlan0 or similar try that. but if that doesnt work let me know. 

i have a similar problem with my notebook however it does not have an eth1 interface, just wlan0. after chaging some things to get ACPI to work, the card got seen by ndiswrapper but the thing wouldnt connect unless i did a bunch of commands manually. i later edited my /etc/network/interfaces to do the stuff at bootup, you may have to do this too.

---

