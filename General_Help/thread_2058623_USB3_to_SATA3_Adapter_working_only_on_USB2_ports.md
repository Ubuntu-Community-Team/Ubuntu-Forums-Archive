---
title: "USB3 to SATA3 Adapter working only on USB2 ports"
date: 2012-09-16
forum: General Help
---

### Post by zoff_ita on 2012-09-16
Hi, 
I recently bought a USB3 to SATA3 Adapter to connect internal disk drives through USB.

It works perfectly when connected to USB2 ports, but when I connect it to a USB3 port it isn't detected at all, nor in lsusb nor, obviously, in fdisk -l.

When detected (on USB2) it is shown as:
```
Bus 002 Device 008: ID 174c:55aa ASMedia Technology Inc.
```

Any idea?

---

### Post by dcstar on 2012-09-17
> **zoff_ita said:**
> Hi, 
I recently bought a USB3 to SATA3 Adapter to connect internal disk drives through USB.

It works perfectly when connected to USB2 ports, but when I connect it to a USB3 port it isn't detected at all, nor in lsusb nor, obviously, in fdisk -l.

When detected (on USB2) it is shown as:
```
Bus 002 Device 008: ID 174c:55aa ASMedia Technology Inc.
```

Any idea?

Your USB3 ports are not supported by Ubuntu.

---

### Post by zoff_ita on 2012-09-17
That would be strange, 'cause USB PenDrives works perfectly on that port.

---

### Post by dcstar on 2012-09-17
> **zoff_ita said:**
> That would be strange, 'cause USB PenDrives works perfectly on that port.

Maybe they are connecting as USB 2 devices.

Usually USB 3 hardware issues are caused by people not connecting the PSU Power lead to the provided connector on the card so the USB 3 ports do not have sufficient power to run true USB 3 devices.

---

### Post by zoff_ita on 2012-09-17
> **dcstar said:**
> Maybe they are connecting as USB 2 devices.

Usually USB 3 hardware issues are caused by people not connecting the PSU Power lead to the provided connector on the card so the USB 3 ports do not have sufficient power to run true USB 3 devices.

I know but I also know how to distinguish an USB2 port from an USB3 port.
I already tried that port on other operating systems and it's working.
So it is not a power issue, in any case I'm connecting a SSD Drive that has a low power requirement.

Sum up:
Same device, same adapter, same port on other OS works, on Ubuntu doesn't.
Any pendrive I have is fully working on that same port, even on Ubuntu.

---

### Post by dcstar on 2012-09-17
> **zoff_ita said:**
> I know but I also know how to distinguish an USB2 port from an USB3 port.
I already tried that port on other operating systems and it's working.
So it is not a power issue, in any case I'm connecting a SSD Drive that has a low power requirement.

Sum up:
Same device, same adapter, same port on other OS works, on Ubuntu doesn't.
Any pendrive I have is fully working on that same port, even on Ubuntu.

Then the original answer stands - the USB 3 hardware is not supported by Ubuntu (actually the Linux kernel) as USB 3, only USB 2.

---

### Post by zoff_ita on 2012-09-17
> **dcstar said:**
> Then the original answer stands - the USB 3 hardware is not supported by Ubuntu (actually the Linux kernel) as USB 3, only USB 2.

Mmmm I can't understand.
Are you telling me that Ubuntu can handle USB3 hardware as USB2 only on USB2 ports?
Why doesn't simply work in "USB2 mode" on USB3 ports?

---

