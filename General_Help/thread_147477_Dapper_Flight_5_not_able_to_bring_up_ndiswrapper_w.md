---
title: "Dapper Flight 5 not able to bring up ndiswrapper wlan"
date: 2006-03-20
forum: General Help
---

### Post by s_groening on 2006-03-20
Havin installed Breezy and upgraded the badger to Dapper Drake Flight 5, I am now experiencing trouble with ndiswrapper 1.10, compiled from source...

The wireless card was detected already, it's a Belkin 11g F5D7000 with a Broadcom chipset detected as eth1, but no driver was installed. 
I installed ndiswrapper 1.10 and added the driver for the interface, now named/aliased eth2, but I could not successfully activate it. It keeps complaining about the lack af a driver and asks me to check that the interface has been properly configured...

Has anyone else had similar problems?

Best regards,
Søren G.

---

### Post by mr.p on 2006-03-20
[QUOTE=s_groening]Havin installed Breezy and upgraded the badger to Dapper Drake Flight 5, I am now experiencing trouble with ndiswrapper 1.10, compiled from source...

The wireless card was detected already, it's a Belkin 11g F5D7000 with a Broadcom chipset detected as eth1, but no driver was installed. 
I installed ndiswrapper 1.10 and added the driver for the interface, now named/aliased eth2, but I could not successfully activate it. It keeps complaining about the lack af a driver and asks me to check that the interface has been properly configured...

Has anyone else had similar problems?

Best regards,
Søren G.[/QUOTE]
This probably best belongs in the "Dapper Drake Development Release" forum.

However, possibly try recompliling ndiswrapper.

---

