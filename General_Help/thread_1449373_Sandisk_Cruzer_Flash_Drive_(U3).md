---
title: "Sandisk Cruzer Flash Drive (U3)"
date: 2010-04-07
forum: General Help
---

### Post by standingwave on 2010-04-07
I picked up one of these at Walmart a couple of weeks ago ($10 for 4GB). I didn't know about the U3 'Smart' software nor was it labeled on the packaging or I wouldn't have bought it. Anyway, this software resides in a non-removable partition and automatically installs itself  onto any Windows PC it is  plugged into where it resides as an optical (?) drive. I hate hate hate garbage like this. 

I tried everything without avail: format, gparted, etc. Sandisk provides removal tools for Win & Mac but not Linux apparently and the Win version didn't work  under WINE (looking for drive letters perhaps?). I was just about to go find a Windows machine to run the removal tool when I found this:

[http://packages.ubuntu.com/lucid/u3-tool](http://packages.ubuntu.com/lucid/u3-tool)

Worked great. Thanks to the developers.

---

### Post by dcstar on 2010-04-07
> **standingwave said:**
> I picked up one of these at Walmart a couple of weeks ago ($10 for 4GB). I didn't know about the U3 'Smart' software nor was it labeled on the packaging or I wouldn't have bought it. Anyway, this software resides in a non-removable partition and automatically installs itself  onto any Windows PC it is  plugged into where it resides as an optical (?) drive. I hate hate hate garbage like this. 

I tried everything without avail: format, gparted, etc. Sandisk provides removal tools for Win & Mac but not Linux apparently and the Win version didn't work  under WINE (looking for drive letters perhaps?). I was just about to go find a Windows machine to run the removal tool when I found this:

[http://packages.ubuntu.com/lucid/u3-tool](http://packages.ubuntu.com/lucid/u3-tool)

Worked great. Thanks to the developers.

Using the "Create partition table" feature in gparted may also work - someone may want to test this next time they have a U3 device.

---

### Post by genieyclo on 2011-07-08
Awesome. Thank you so much. **This** is an excellent thread, you had an issue you thought others might come across, clearly labeled the problem and steps you went through and proactively found and explained your solution. Kudos to you. Rest assured other searchers like myself have benefited. Thanks so much for keeping open source awesome.

---

