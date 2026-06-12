---
title: "Completly noobish, can't connect to internet?"
date: 2009-11-12
forum: General Help
---

### Post by Rendil on 2009-11-12
So I tried running kubuntu, but it never noticed my 2wire internet dongle, so I switched over to ubuntu.
Ubuntu (I think) recognizes it, because the light on the dongle shows up. (but who knows, maybe that means nothing.) 
But I can't connect. If I hit the internet... thing (see, noob. Sorry, if the computer with ubuntu wasn't all the way over there *points* I'd get up and find the technical term for it.) no connection shows up. It gives me the options to connect by adding and inputting the ssid and bssid, but I don't know how to look those up. I tried in the terminal doing the sudo iwlist command, but it told me something to the effect that it didn't support that function. 

Please help, and speak slowly. I have a headache.

---

### Post by P4man on 2009-11-12
Is this a mobile broadband connection, or a wifi dongle ?

---

### Post by Rendil on 2009-11-14
I belive it's wifi. How would I tell the difference?

---

### Post by jeb800e on 2009-11-14
Try NDISWRAPPER. 
Go to Synaptic Package Manager and type "ndis" in the search box. Check "ndisgtk" and "ndiswrapper-common". This should automatically check the "ndiswrapper-utils-1.9", also, and possibly a few others.

Once installed go to System < Administration < Windows Wireless Drivers. Follow the on-screen instructions.

---

### Post by P4man on 2009-11-15
> **Rendil said:**
> I belive it's wifi. How would I tell the difference?

A wifi dongle would connect to an access point at home, which is connected to the internet by a fixed internet connection (adsl, cable,..)

A wireless broadband is supplied to you typically by your mobile phone operator and should work anywhere using GSM or similar infrastructure.

Either way, lets find out. have the stick plugged in, and open a terminal from applications > accessoiries. Then type

```
lsusb
```
(that is LSUSB in lowercase)

Copy paste the output here, that should tell us exactly what you have.

---

