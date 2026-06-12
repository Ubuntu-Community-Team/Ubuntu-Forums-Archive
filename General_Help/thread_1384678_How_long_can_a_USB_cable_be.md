---
title: "How long can a USB cable be?"
date: 2010-01-18
forum: General Help
---

### Post by Silvernail on 2010-01-18
I would like to put my webcam up and upstream to 'ustream' to show my ponies playing. 

The distance between my computer and the stable is about a 100 feet. Is there enough power to push the signal that far or do I need to put a booster along the route.

---

### Post by mouseinahaze on 2010-01-18
The USB 2.0 spec says about 16 feet, so running 100 foot of usb might not be feasible. Have you looked into getting an Ethernet camera? Ethernet is good out to 100 Meters or about 300 feet.

---

### Post by TBABill on 2010-01-18
Or a wireless webcam to a USB hub at the computer?

---

### Post by Silvernail on 2010-01-18
> **mouseinahaze said:**
> The USB 2.0 spec says about 16 feet, so running 100 foot of usb might not be feasible. Have you looked into getting an Ethernet camera? Ethernet is good out to 100 Meters or about 300 feet.

The 16 feet, do you know if it is a power issue or a timing issue?

---

### Post by Ahriman on 2010-01-18
AFAIK, it's a problem of not enough signal getting through that distance clear enough. Same with ethernet at long distances (500m+, eg.). You might get *some* signal over that distance, but it wouldn't be reliable.

We are currently using wireless security cameras here at work, and they are transmitting quite well at a distance of about 25 meteres (just under 100 feet), through 2 brick walls and some machinery. That's another option ...

---

### Post by pirateghost on 2010-01-18
i have a usb>ethernet>usb extender that i use for a total distance of about 40 ft.  works great

[http://www.newegg.com/Product/Product.aspx?Item=N82E16800997018](http://www.newegg.com/Product/Product.aspx?Item=N82E16800997018)

i have some similar to those, but they can be found much cheaper by shopping around.  monoprice.com might have some.  specs say you can go up to about 198ft with them

---

### Post by cgb on 2010-01-18
I've heard you can run with USB Repeater Cables for up to about 80 feet, 5 x 16' cables.  I've myself only tried going as far as 3 cables, 48 feet, with no problems.

---

### Post by bkratz on 2010-01-18
> **pirateghost said:**
> i have a usb>ethernet>usb extender that i use for a total distance of about 40 ft.  works great

[http://www.newegg.com/Product/Product.aspx?Item=N82E16800997018](http://www.newegg.com/Product/Product.aspx?Item=N82E16800997018)

i have some similar to those, but they can be found much cheaper by shopping around.  monoprice.com might have some.  specs say you can go up to about 198ft with them

The actual spec is about 16 feet for reliable communications as an earlier poster said. With usb the difference between a 1 and 0 is a very small differential voltage which is easily lost, actually the use of any extension does not meet specs.

---

### Post by pirateghost on 2010-01-18
> **bkratz said:**
> The actual spec is about 16 feet for reliable communications as an earlier poster said. With usb the difference between a 1 and 0 is a very small differential voltage which is easily lost, actually the use of any extension does not meet specs.
it may not 'meet specs' but i have used these before on a webcam with about 100' of cat5e in between and it worked great (right now im using one with my vyatta box running lcdproc connected to a matrix orbital 4x20 lcd).  the webcam was a logitech that had face recognition and everything worked better than expected.  i honestly didnt think that it would go that long of a distance, but it did.  just sharing real world experiences rather than spouting off specs and requirements....

---

### Post by Leppie on 2010-01-18
use an IP cam, easiest solution ;)

---

### Post by bkratz on 2010-01-18
> **Silvernail said:**
> The 16 feet, do you know if it is a power issue or a timing issue?

Well I just looked it up, it actually is more a timing issue.

A:   Even if you violated the spec, it literally wouldn't get you very far. Assuming worst-case delay times, a full speed device at the bottom of 5 hubs and cables has a timeout margin of 280ps. Reducing this margin to 0ps would only give you an extra 5cm, which is hardly worth the trouble.

Note the 280 pico second time.

---

### Post by audiomick on 2010-01-18
> **bkratz said:**
> The actual spec is about 16 feet for reliable communications as an earlier poster said. With usb the difference between a 1 and 0 is a very small differential voltage which is easily lost, actually the use of any extension does not meet specs.

That's for usb alone. If you convert to ethernet, as pirateghost suggested, you can do 100 metres on CAT5 cable before it has to go through a router, in which case you can head for your next 100 metres. If you convert to fibre optics, it will go for at least 1000 metres, and I am pretty sure more. Then back to USB at the other end for less than 3 metres.

---

### Post by bkratz on 2010-01-18
> **audiomick said:**
> That's for usb alone. If you convert to ethernet, as pirateghost suggested, you can do 100 metres on CAT5 cable before it has to go through a router, in which case you can head for your next 100 metres. If you convert to fibre optics, it will go for at least 1000 metres, and I am pretty sure more. Then back to USB at the other end for less than 3 metres.

The original OP asked about the distance with USB, of course you can add additional drivers and change to either RS485 or ethernet and get more distance, but that is not what was asked.

---

### Post by cgb on 2010-01-19
The 16' rule is true for standard passive USB Cables but Active USB cables can be run for longer distances.  Even so, though, 100' would be quite pushing it.  

[http://www.belkin.com/IWCatProductPage.process?Product_Id=160362](http://www.belkin.com/IWCatProductPage.process?Product_Id=160362)

---

