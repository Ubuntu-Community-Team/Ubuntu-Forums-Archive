---
title: "brightness controls, nothing works"
date: 2012-09-25
forum: General Help
---

### Post by unuscione on 2012-09-25
I've installed Ubuntu 12.04 32 bit on a partition next to Vista, on a desktop PC, with Grub bootloader.

Still, I'm new to Linux / Ubuntu, and there's parts I can't figure.

I've tryed every way I could find on www to change the brightness: none works except the xgamma command.
I'm not sure if it's normal, being this a desktop that there is no /sys/class/backlight/
That directory doesn't exist on my insallation: does it get installed only if the computer is aknowledged as a laptop?

---

### Post by unuscione on 2012-09-25
I found the files brightness and max_brightness, they got installed in /sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/leds/xpad0/
the directory with the Xpad controller drivers, in fact, when I change the brightness by therminal with 
echo n > /sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/leds/xpad0/brightness
the led in the center of the controller blinks.

I've tryed to move the files in the backlight dir but I get an error, I suppose I don't have the privileges to copy / paste files in the sys directory
:(

---

