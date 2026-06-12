---
title: "Toshiba Laptop runs hot"
date: 2010-07-14
forum: General Help
---

### Post by jwdv22 on 2010-07-14
I have installed Ubuntu 10.04 and configured it pretty well. However my laptop was getting hot. I ran powertop and I get this

Top causes for wakeups:
  48.6% (402.7)   [uhci_hcd:usb3, uhci_hcd:usb4, uhci_hcd:usb5, sky2@pci:0000:01:00.0, ipw2200, yenta, i915@pci:0000:00:02.0, ohci1394, mmc0, mmc1, mmc2] <in

i915 is my chipset from Intel. Started another thread about this but was told to start another one, so I apologize if it seems like I am double posting.

So this led me to start Googling and I saw that some people had relieved this problem by installing Intel drivers, but Intel doesn't supply drivers for Linux anymore, [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/) does.

I having a few problems following their installation instructions I think because they are writtne for Fedora, but probably because I am a novice and have no idea what I am doing ;)

If any one could help I would appreciate it. OH and when I say hot, Xsensors says temp1 is running at 75 degrees C and temp 2 is 54

---

### Post by m4tic on 2010-07-14
Do you get the same issue in Windows? If so look for a BIOS update

---

### Post by jwdv22 on 2010-07-14
> **m4tic said:**
> Do you get the same issue in Windows? If so look for a BIOS update

No, used to be a work laptop they gave me. Used XP on it for 3 years, ran fine.

---

### Post by iponeverything on 2010-07-14
75 is very hot, try putting a vacuum cleaner hose up to vent when the machine is off to see if you clear dust that might be clogging up the heat sink. 

75 C sustained will probably cause laptop fail.

---

### Post by jwdv22 on 2010-07-14
> **iponeverything said:**
> 75 is very hot, try putting a vacuum cleaner hose up to vent when the machine is off to see if you clear dust that might be clogging up the heat sink. 

75 C sustained will probably cause laptop fail.

Yeah. That is why I was hoping someone could help me with the driver installation. Otherwise it is back to XP.

---

### Post by HermanAB on 2010-07-14
For Toshiba, add acpi_osi="Linux" to your kernel boot line in grub menu.lst file.

---

### Post by jwdv22 on 2010-07-14
> **HermanAB said:**
> For Toshiba, add acpi_osi="Linux" to your kernel boot line in grub menu.lst file.

I don't have the file in /boot/grub/

*edit* so I created a menu.lst file , but I am unsure of the kernel boot line.

rebooted after creating file. Also I checked and I have the most recent bios

---

