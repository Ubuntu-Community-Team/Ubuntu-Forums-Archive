---
title: "Can a Keyboard be incompatible with Linux?"
date: 2012-09-10
forum: General Help
---

### Post by SuperFreak on 2012-09-10
I just purchased a mechanical Levitron Click  keyboard (KB528U) by Azio and can't get it to work on my Ubuntu box. The box it came in says it is compatible with IBM PCs using Windows but there is no mention of Linux. I never thought that a keyboard could be OS dependent.
The keyboard funtions fine in BIOS but as soon as Ubuntu starts it is inoperable. It is a USB type keyboard. Has anyone used this keyboard successfully in Ubuntu?

---

### Post by Vaphell on 2012-09-10
some functions can be OS dependent (like support for media keys enabled by the driver, etc) but i don't think it should completely die when in linux, considering it works fine before boot phase when no OS is present.

---

### Post by SuperFreak on 2012-09-10
It is funny. I have rebooted twice into BIOS and it works, when I load Ubuntu it doesn't
I don't suppose the fact that it is a mechanical keyboard (used mainly by gamers) has anything to do with it?

---

### Post by cortman on 2012-09-10
> **SuperFreak said:**
> It is funny. I have rebooted twice into BIOS and it works, when I load Ubuntu it doesn't
I don't suppose the fact that it is a mechanical keyboard (used mainly by gamers) has anything to do with it?

Does that USB port work with anything else in Ubuntu?
Could be it's not recognizing it or loading the proper driver.

---

### Post by jerrrys on 2012-09-10
Is this a possibility?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/990870](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/990870)

---

### Post by SuperFreak on 2012-09-11
> Is this a possibility?

[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/990870](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/990870)

I don't think that is the problem as I have unplugged the keyboard while in Ubuntu and plugged it into a different USB port to no avail. Probably of no importance but this is a desktop.


The USB port works fine with external drives and other devices

---

### Post by SuperFreak on 2012-09-15
bump

---

### Post by SuperFreak on 2012-09-21
I entered command "lsusb" and got this out put with keyboard plugged in and then with keyboard not plugged in:

```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f9:01f5 Brother Industries, Ltd 
Bus 002 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 005: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 003 Device 002: ID 04d9:a055 Holtek Semiconductor, Inc. 
david@david-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f9:01f5 Brother Industries, Ltd 
Bus 002 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 005: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse

```


So I would assume that the keyboard is "Holtek Semiconductor, Inc." but I don't understand why it won't function. If anyone has an idea how I can get it to work let me know

Thanks

---

### Post by oldfred on 2012-09-21
My first USB keyboard worked in Windows & Ubuntu but not grub. I had to use an adapter to the ps/2 port just to work in the grub menu.

But there was a BIOS setting to implement USB keyboard & mouse. Have you checked settings in BIOS?

---

### Post by SuperFreak on 2012-09-21
I had a look in BIOS.I found a setting for "USB Keyboard/remote Power on" which I enabled but it didn't make any difference. Also Legacy USB Support is set to enabled. I guess I should have been more careful with the purchase; the ad said the keyboard was supported by Windows Vista and 7 but no other non Windows operating systems were listed. I just thought all keyboards would work with any OS. This will likely be an Ebay item for sale now.
Thanks for your interest OldFred

---

### Post by SuperFreak on 2012-09-21
Just got an email from the manuafacturer:

> Sorry for missing your message earlier. Unfortunately, the KB528U Clicker
Mechanical Keyboard does not work in Linux. The reason being is the NKRO
chipset is not compatible with Linux. The NKRO chipset is responsible for
the anti-ghosting gaming features found on this keyboard.

---

