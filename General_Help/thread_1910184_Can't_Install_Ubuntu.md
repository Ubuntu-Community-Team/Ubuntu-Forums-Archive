---
title: "Can't Install Ubuntu"
date: 2012-01-16
forum: General Help
---

### Post by Meatek on 2012-01-16
I'm trying to install Ubuntu on my new system, but it hangs trying to boot. The last line is always something like:*  [I]usb 2-1.7*: *new* full speed USB device using ehci_hcd, [/I]and then it hangs there. It seems detect my keyboard and mouse, then stop. I've never had problems installing Ubuntu or using livecds until now...

i5 2500k @ 4.0ghz
EVGA 570gtx
16gb DDR3 RAM
ASUS P8Z68-V

Any help would be appreciated.

---

### Post by Maximus559 on 2012-01-16
Have you tried all the obvious steps? E.g., remove all PCI cards, disconnect all nonessential peripherals, try using a different keyboard and mouse, etc? Last time I had trouble booting, it turned out to be my PCI wireless adapter. Traded it for a different one and problem was solved. In your case, though, it sounds like a USB peripheral device may be to blame.

---

### Post by Meatek on 2012-01-16
The only pci device is my graphics card, and the only things hooked up to usb are my keyboard and mouse. When I tried it with them unplugged it stalled at the same place, but when I plugged them in it recognized them.

---

### Post by Rebelli0us on 2012-01-16
In Ubuntu software center there is an app "Device manager", it will tell you exactly which device is on USB2.1

---

### Post by Maximus559 on 2012-01-16
> **Rebelli0us said:**
> In Ubuntu software center there is an app "Device manager", it will tell you exactly which device is on USB2.1

That's not going to do him much good if he can't get Ubuntu to boot.

To the OP: you might try fiddling with the USB settings in your BIOS. There are usually some options related to the USB controller and USB legacy support.

---

### Post by Meatek on 2012-01-16
Legacy support was enabled, didn't work. Here's the actual line it stops at:

*[4.711946]  [I]usb 2-1.7*: *new* full speed USB device number 5 using ehci_hcd

[/I]It's usb 3.0 if that makes a difference.

---

### Post by Serpher on 2012-01-16
Keep in mind with newer hardware, especially motherboards, there is a fair risk that the Linux kernel Ubuntu uses doesn't support your hardware. Perhaps try a distro's live CD with a more cutting edge kernel like Fedora 16 to see if it works.

---

