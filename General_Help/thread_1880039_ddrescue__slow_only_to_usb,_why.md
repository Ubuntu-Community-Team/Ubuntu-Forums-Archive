---
title: "ddrescue : slow only to usb, why?"
date: 2011-11-12
forum: General Help
---

### Post by Tr4sHCr4fT on 2011-11-12
a girlfriend of mine has headcrashed her netbook, im currently on to rescue it.

it's acessible and the bits are still good in the important userdata drive areas.
but so far ddrescue is painfully slow with average **1.5MB/s** to an usb attached equal hdd
googling this results "ddrescue is slow cuz the drive dies" but:

if i ddrescue straight to dev0 it runs at **full sata speed**!
and dd from zero to my external drive averages around to **22MB/s** like under Windows

so it seems either be a USB 2.0->1.1 problem nor the target drive itself
i tried even piping dd_rescue (the predecessor) to split for writing 4GB chunks on an other, fat32 formatted usb drive, and it results at still good 11MB/s. [SIZE=1](which will be my last resort tomorrow, as the Netbook will be collected for RMA on Monday, and the copy must be finished until there, which is impossible to achieve with 1,5MB/s only[/SIZE])

Any of the good guys here in for a hint? while my time is running away...


// no i cant pull out the damaged hdd to connect it on sata directly - warranty void sticker :(

---

### Post by Tr4sHCr4fT on 2011-11-13
*push*

---

