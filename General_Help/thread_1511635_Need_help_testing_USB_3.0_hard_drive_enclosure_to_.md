---
title: "Need help testing USB 3.0 hard drive enclosure to see why it won't connect."
date: 2010-06-17
forum: General Help
---

### Post by TheOnlyMrK on 2010-06-17
I bought a 2.5inch hard drive ( [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136197](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136197) ) and a USB 3.0 enclosure ( [http://www.newegg.com/Product/Product.aspx?Item=N82E16817392038](http://www.newegg.com/Product/Product.aspx?Item=N82E16817392038) ) for it from NewEgg and just recieved it today, put it all together all happy cause I'm a computer nerd like that xP and plugged it in to the USB 3.0 port on my computer only to have... nothing happen. I checked the drivers were installed (The computer runs Windows 7), that USB 3.0 was enabled in BIOS, jiggling the cables around, and all that but no luck. I then plug it into a USB 2.0 port and it works fine, enclosure is installed as is the hard drive in it and HDTune Pro reports absolutely no errors. I opened the enclosure and looked over the PCB real close, not a single broken solder, melting/burning, or anything like that, the USB 3.0 cable appears to be fine and so on, so I put it all back together and booted from my Ubuntu 10.04 64bit LiveCD, clicked the try option and once it was done starting up I plugged the enclosure into the USB 3.0 port and once again, nothing.

At this point I'd take the hint that it's the enclosure or the cable for the enclosure not working but as a last resort before I return it to NewEgg I wanted to ask all of you if you could help in any way to find where this is messing up? I know their is a way to "scan" for hardware in the console on Ubuntu but I can't remember it and was wondering if that would be useful?

---

### Post by TheOnlyMrK on 2010-07-01
Anyone?

---

### Post by varunendra on 2010-07-01
You put the question two weeks ago & still struggling with it?

I'd suggest you to check the enclosure on someone's working USB3 interface or check some other working USB3 device on your computer's USB3 interface to determine whether the problem is in the enclosure or in your computer itself (some config. maybe?).

Else return it to NewEgg if you still can.

---

### Post by TheOnlyMrK on 2010-07-01
> **varunendra said:**
> You put the question two weeks ago & still struggling with it?

I'd suggest you to check the enclosure on someone's working working USB3 interface or check some other working USB3 device on your computer's USB3 interface to determine whether the problem is in the enclosure or in your computer itself (some config. maybe?).

Else return it to NewEgg if you still can.
I already returned the enclosure to NewEgg and got a replacement, and it's the same thing as last time. So the only thing I can think of is something is wrong with my motherboard.

---

### Post by EuriskoXP on 2011-07-05
try 
"sudo lsusb"
and post what you get

---

