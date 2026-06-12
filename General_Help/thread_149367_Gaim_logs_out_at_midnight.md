---
title: "Gaim logs out at midnight"
date: 2006-03-23
forum: General Help
---

### Post by RicJD on 2006-03-23
Does anyone else have the problem of gaim logging them out at midnight?  I do and it's quite anoying.  Has any body whose had this been able to fix it? Or does anyone have any idea on how to fix it?

---

### Post by neoginn on 2006-03-23
this used to happen to me, but it turned out that it was not GAIM but my network connection. so you may want to trouble shoot that area first.

---

### Post by dmizer on 2006-03-23
also, i'm not sure which service you are using through gaim (aim, msn ...) but i know that with aim, sometimes around midnight they will shut down the server for mantinence.  if you are using the actual aim client, you will receive a warning message something to the effect of "the aim service will be temporarily shut down in _____ minutes."  but you don't get that message with gaim.

this is a fairly regular occurance with the aim service.

alternatively, you can check your dmesg to see if your internet connection was temporarily interupted.  i also highly suggest that you include the plugin for auto reconnect.  it's already included with the gaim package, so all you have to do is enable it by going to: tools > preferences > plugins > put a checkmark next to "Auto-reconnect".

i believe that may solve your problem.

---

