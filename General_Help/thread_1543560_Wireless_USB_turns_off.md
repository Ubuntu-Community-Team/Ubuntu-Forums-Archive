---
title: "Wireless USB turns off?"
date: 2010-08-01
forum: General Help
---

### Post by cableguy414 on 2010-08-01
I'm running Ubuntu 10.04 with a Belkin USB wireless NIC and using the NDIS/WIndows drivers.

The odd problem I'm having is it seems that the wireless turns off.  When I try to connect to my wireless (or any wireless for that matter), it doesn't see any wireless networks, at all.

Sometimes unplugging and re-plugging the USB NIC will wake it up and it will work again, other times, I just need to do a full reboot.

Any thoughts on what might be doing this? Or how I might be able to find the cause?

I don't see anything glaring in the log file.

UPDATE: I removed network-manager and installed wicd and I'm still having the same issue.  The wireless will die.  No wireless networks show up at all.

Thanks.

---

### Post by cableguy414 on 2010-08-03
I think I figured out my issue.  It's a bug(?) in ndiswrapper.  According to the Wiki for my USB NIC: 

"Works fine. Stops working from time to time requiring an unplug-replug."

Personally, I wouldn't consider this as "working fine".

I guess I need to figure something else out, or go back to using the built-in driver, even though I don't get full speed out if the NIC.

Thanks.

---

