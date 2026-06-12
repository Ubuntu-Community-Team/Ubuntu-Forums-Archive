---
title: "Ubuntu 12.04/Sierra Wireless USBConnect Mercury 3g modem"
date: 2012-07-04
forum: General Help
---

### Post by nataraj88 on 2012-07-04
I have an older Sierra Wireless USConnect Mercury 3g modem with AT&T service which is provided for me my one of my clients.  As far as I know there is no login information required for it.  I got it to work under 10.04 by adding the following entry to /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi

```
229a230,239
> 	<!--Sierra Wireless USBConnect Mercury -->
> 	<match key="@info.parent:usb.product_id" int="0x6880">
> 	  <match key="@info.parent:usb.interface.number" int="3">
> 	    <match key="serial.port" int="3">
>               <append key="modem.command_sets" type="strlist">GSM-07.07</append>
>               <append key="modem.command_sets" type="strlist">GSM-07.05</append>
> 	    </match>
> 	  </match>
> 	</match>
> 

```

When I connect it to 12.04 the network manager recognizes it but wants me to provide login information which I don't have.  How can I get this modem to work under 12.04 without providing login information?

Thank You,
Nataraj

---

### Post by nataraj88 on 2012-07-04
I installed the hal-info package and was then able to install the entry for my modem and get it to work.

Nataraj

---

