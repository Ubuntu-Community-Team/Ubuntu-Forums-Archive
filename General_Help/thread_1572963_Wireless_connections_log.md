---
title: "Wireless connections log"
date: 2010-09-12
forum: General Help
---

### Post by samuelmaskell on 2010-09-12
Hello,
Sorry if this has been posted already.  I searched but couldn't find what I was looking for. Maybe I was just searching the wrong thing.

Anyway, here's my situation.

I recently moved in with my friend and I cannot seem to connect to his wireless network on my desktop in linux.  However, I can connect with my laptop(in both windows and linux), my phone and my desktop in windows. 

Of course, the first thing that you would check would be drivers.  However, I was able to connect with this same desktop at my old place.  Also, I can create a wireless hotspot with my Nexus One and my desktop can connect to that.

So here's my question.

Is there a way for me to see a log of what happens when I try to connect to this network?  I try to connect and it sits there for a minute or two and then prompts me to re-enter the password.  It would be really nice if I could see what exactly isn't working.

btw, I'm using a D-Link DWA-140 wireless usb adapter with NDIS wrapper.
Before using NDIS wrapper I tried this [http://sudosys.be/?q=D-Link_DWA_140_ubuntu](http://sudosys.be/?q=D-Link_DWA_140_ubuntu).  It may be possible that I'll need to revert some of the changes I made then in order to get it to work now..

Thanks,
Samuel Maskell

---

### Post by Lukas666 on 2010-09-12
How about this?

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by wojox on 2010-09-12
Did you remove/purge all the config files from your old place?

Is your desktop wireless?

---

### Post by samuelmaskell on 2010-09-12
I tried looking through that ubuntu help page and I didn't see anything that looked all that helpful.  Maybe I'm wrong though.  It just seems like it's talking about setting up drivers but I really don't think it's a problem with drivers as I can connect to other networks.


wojox, what config files would you suggest removing?
and yes, it is wireless.  I'm using the d-link dwa-140 wirless usb adapter

---

### Post by wojox on 2010-09-12
> **samuelmaskell said:**
> I tried looking through that ubuntu help page and I didn't see anything that looked all that helpful.  Maybe I'm wrong though.  It just seems like it's talking about setting up drivers but I really don't think it's a problem with drivers as I can connect to other networks.


wojox, what config files would you suggest removing?
and yes, it is wireless.  I'm using the d-link dwa-140 wirless usb adapter

I was thinking whatever you used before in Network Connections > Wireless Connections.

---

