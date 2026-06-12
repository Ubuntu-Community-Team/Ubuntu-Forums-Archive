---
title: "Connecting to Shared Printer w/ 12.04"
date: 2012-08-26
forum: General Help
---

### Post by gjrepicky on 2012-08-26
We have a desktop running 10.04, w/ an HP Laserjet 1212mp printer shared so that everyone in the family can use it.  We've had no problems accessing this printer over our home network -- connection has been effortless with multiple machines running various releases of Ubuntu.  Upgraded my laptop to 12.04, and cannot "see" this printer on the network, nor have I figured out a way to address it despite a morning's search of the internet.

Thanks,

George

---

### Post by gjrepicky on 2012-08-26
Solved it -- more bumbling than logic.

Found printer URL on the 10.04 machine.
Managed to address printer using this url on 12.04 machine.
Printer didn't work -- in response to error message, installed HPLIP from HP website.

But...,

While HPLIP was installing, found that if the "Printing" window was active, clicking on the notification area revealed a series of menus, one of which allowed the user to "View Discovered Printers" -- voila, there eas my printer!  A click .... and it works!!!!!  I don't know if any of the previous stuff was needed.

Hope my (mis?)adventure saves someone else some trouble!

The more I use 12.04 & Unity, the more I think there may really be some neat stuff here -- but finding it is sometimes challenging!

George

---

### Post by gjrepicky on 2012-08-26
Woops!  Forgot to mention that in the above, under "Server", you have to go to "Settings" and check "Show printers shared by other systems."

George

---

