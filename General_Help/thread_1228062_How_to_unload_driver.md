---
title: "How to unload driver?"
date: 2009-07-31
forum: General Help
---

### Post by iamgoose on 2009-07-31
I'm trying to find out how to unload a driver called pl2303. I'm running VMware Workstation 6.5 on Ubuntu 9.0.4. Win XP is the guest OS. I have a usb-to-serial cable for connecting a device in the guest OS. Both Ubuntu and XP recognize the cable (as a "prolific USB" cable) and it is connected in the VM, but Ubuntu shows a dialog saying the device won't work because driver pl2303 in Ubuntu has a claim on the device, and to unload the driver. How?

My interpretation of this is that even though the usb-to-serial cable is recognized by XP, it can't connect to the actual peripheral device for which the cable is needed until I get Ubuntu not to recognize the device - by unloading its driver.

Thanks in advance!

---

