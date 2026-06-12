---
title: "ACPI Problems with P5Q Premium?"
date: 2009-09-12
forum: General Help
---

### Post by Marsupilani on 2009-09-12
Hardware:
- Mainboard ASUS P5Q Premium BIOS 2001
- Processor Q9550
- 8GB RAM
- 750W BeQuiet PowerSupply (already changed)
- 5 SATA Seagate 1TB (ST3100333/ST3100340) + 2 IDE Hitachi (250GB)
-Keyboard G15 with Logitech Optical Mouse
-Netzteil BeQuiet 750W

Software:
-Ubuntu 9.04 (JAUNTY) x64

Problem:
If I connect Keyboard and Mouse to the 2 first Port near the PS/2 Port the Ubuntu Installation reboot after detection of the Keyboard (under ASUS FirstGate/Grub no Problems with the keyboard/mouse!)

Same connections under P5Q Deluxe hadn't any Problems
If I connect Keyboard and Mouse to 2 other USB-Ports I hadn't an Problems under Ubuntu.

The Kernel switch acpi=off cleans the problems, too.

Under Knoppix 6.0.1 I haven't any problems when I use the first 2 USB-Ports for the devices.

After a successfully boot I haven't any problems with the Board, even with extreme load of the cpu!

After any successfully boot I couldn't find any traces about the unsuccessfully boot in messages/dmessages/boot.

Are there any known ACPI-Problems with this HW known?

---

### Post by cariboo on 2009-09-12
This really isn't a server question. moved to General Help.

---

