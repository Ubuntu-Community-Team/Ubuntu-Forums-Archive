---
title: "mdadm RAID degraded"
date: 2011-10-20
forum: General Help
---

### Post by JasonFWard on 2011-10-20
I am confused by mdadm functionality.

I have been playing with this utility and have read a number of articles and help pages on mdadm.

Everything seems fine, yet every RAID array I have created starts by being degraded and repairing.

This "repairing" takes many hours (16 plus hours seems quite normal) yet none of the articles or help pages mentioned this issue.

If I reboot the machine at anytime before this repairing is complete, the repairing ceases and only doing something like formatting the array causes it to restart again from the beginning.

Also, rebooting has the array move from /dev/md0 to /dev/md127 for no apparent reason.

So is this all correct?  It seems strange to me, having set up arrays in Windows I'm used to them working fully once configured and only going into a degraded state if there is some subsequent failure, it all seems odd and broken behaviour to me, since I have to wait 16 plus hours before I can continue to configure and install the machine.

Also will the array randomly move from /dev/md127 to somewhere else at some stage too?

---

