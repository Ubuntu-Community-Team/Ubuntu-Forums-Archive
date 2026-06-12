---
title: "Broadcom 4318 (B43)"
date: 2009-07-29
forum: General Help
---

### Post by Chrismc1 on 2009-07-29
Hi All

I was wondering if there was any better driver than b43 for bcm4318 [airforce1 54g]. I have an aspire 3680 (old i know) and the wlan seems really slow. my connection speed is 1mb/s. I tried 

sudo iwconfg wlan0 rate 54m

this changes the connection information but does not make it any better. Also have read about acer acpi but do not know how to install or even if it is needed as 9.04 has acpi already. 

I have kernel 2.6.28-11 (fresh install). have tried Hardware Drivers, bcm43xx, ndiswrapper.

Is there an alternative with a better connection?

---

### Post by regala on 2009-07-29
> **Chrismc1 said:**
> Hi All
I was wondering if there was any better driver than b43 for bcm4318 [airforce1 54g]. I have an aspire 3680 (old i know) and the wlan seems really slow. my connection speed is 1mb/s. I tried 

sudo iwconfg wlan0 rate 54m


Don't forget the fact that your wifi router has to be capable of sustaining such a load, and for instance a wrt54g from Linksys may be 54g
capable, it can't go faster than 2 MiB/s.
so it may not be a problem of driver.
Besides, there's no other free driver than b43 and b43-legacy, and b43 is undoubtedly the best.


> 
Is there an alternative with a better connection?


as said above, there's likely to be no actual problem with your driver,  802.11g is first an operation mode for the router and client to use, that can theoretically sustain 54Mbits/s.

---

### Post by Chrismc1 on 2009-07-29
My wlan is working but i was just wondering if there was any better, it just seems to hang alot when loading and it never crossed my mid that it could be the router. 

i should think the router can handle 54mb as it doesnt just hang on my network it hangs on a friends aswell.

never mind

Thats why im the noob and you gave a reasonable explaination. ha ha ha.

thanks very much for the reply regala

---

