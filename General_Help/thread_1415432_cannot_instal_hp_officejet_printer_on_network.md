---
title: "cannot instal hp officejet printer on network"
date: 2010-02-24
forum: General Help
---

### Post by workshop1702 on 2010-02-24
hi i cannot install my  officejet d155xi on ubuntu  the printer is connected to my router by cable . i have tried several tutorials on the net and had no luck with any of them i tried through terminal and this is what happens
HP Linux Imaging and Printing System (ver. 3.9.8)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=mdns)
error: No devices found on bus: net
Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=slp)
/error:  Unable to locate the HPLIP Fax PPD file:  HP-Fax-hpcups.ppd.gz  Fax setup has been disabled.
error: Unable to communicate with device (code=12): hpfax:/net/officejet_d_series?ip=192.0.0.192
error: Unable to communicate with the device. Please check the device and try again.
error: Unable to communicate with device (code=12): hpfax:/net/officejet_d_series?ip=192.0.0.192
error: Unable to communicate with the device. Please check the device and try again.

Done.


has anyone any ideas what the problem is and how i can fix it

---

### Post by warp99 on 2010-02-24
You can get all of that information directly from HP:

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Since the print drivers already come with Ubuntu you can skip the parts about downloading anything and go straight to the howto and help guides.

---

