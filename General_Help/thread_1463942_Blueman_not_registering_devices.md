---
title: "Blueman not registering devices"
date: 2010-04-27
forum: General Help
---

### Post by Dooley on 2010-04-27
I have a usb bluetooth dongle I've connected to my machine.

The device appears just fine and using hcitool scan I can scan for device with no trouble.

However blueman doesn't seem to register the device even when I force the applet to display and try add a new device it won't scan/see any of the bluetooth devices.

Has anyone come across something similar or would know how I should proceed?

---

### Post by fragos on 2010-04-27
Some devices are indiscoverable unless specifically commanded to so and discover-ability may then be on timer. Some devices are very finicky about pairing and you may have to try multiple times to get pairing done. I've had no trouble with Blueman.

---

### Post by Dooley on 2010-04-28
Sorry I may not have explained myself right.

hcitool scan -> returns output of all bluetooth devices(with mac addresses), which is exactly what I want. Ie scanning works.

blueman scan -> returns nothing and I know the devices in question are still running and discoverable(the hcitool scan would prove that no?), so I can't add devices etc.

---

