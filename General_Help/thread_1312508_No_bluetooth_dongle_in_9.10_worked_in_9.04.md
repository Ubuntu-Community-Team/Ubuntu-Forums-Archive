---
title: "No bluetooth dongle in 9.10 worked in 9.04"
date: 2009-11-03
forum: General Help
---

### Post by yopnono on 2009-11-03
Ok here we go.
Using a bt logitech mini dongle, and it worked fine in 8.xx - 9.04.
But now after a clean install of the 9.10 the bt is not found any more of the system.

hci scan = Device is not available: No such device

lsusb = Bus 004 Device 008: ID 046d:c714 Logitech, Inc. 
Bus 004 Device 007: ID 046d:c713 Logitech, Inc. 
Bus 004 Device 006: ID 046d:0b04 Logitech, Inc. 

bluetooth-properties = there is no adapter!!

Any ideas?

//Mike

---

### Post by yopnono on 2009-11-04
No? No ideas?!

---

### Post by yopnono on 2009-11-04
downgraded to jaunty bluetooth package, it works kind of.

---

### Post by fragos on 2009-11-04
I've a TRENDnet Bluetooth dongle that has worked for me in the past. I did have some issues with Bluetooth and (.10 but they were cleared up by installing blueman which replaces the gnome Bluetooth manager.

---

### Post by yopnono on 2009-11-05
> **fragos said:**
> I've a TRENDnet Bluetooth dongle that has worked for me in the past. I did have some issues with Bluetooth and (.10 but they were cleared up by installing blueman which replaces the gnome Bluetooth manager.

Yep much better thanks :)

---

