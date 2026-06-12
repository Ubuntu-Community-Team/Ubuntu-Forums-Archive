---
title: "How to install new hardware?"
date: 2006-04-24
forum: General Help
---

### Post by PriceChild on 2006-04-24
Hey, my RT2500 wireless network card wasn't picked up when i installed Breezy, it was last time perfectly!

I've replaced the card with one i know to work, just incase, but still it doesn't show up in network manager.

I'm guessing this doesn't work automatically and i would really like to know how to get ubuntu to look at all my hardware again :)

Thanks for any help, Pricey

---

### Post by opus on 2006-04-24
Does it show up in the Networking applet?

Click System->Administration->Networking.  Check if your card is listed there.  If so, go to the properties, click the Enabled checkbox, and configure the wireless settings.

Probably the same scenario for the other card.

Aaron

---

### Post by PriceChild on 2006-04-24
Nope, not shown anywhere.

Fixed it by installing the rt2500 modules using the module assistant.

---

