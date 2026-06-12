---
title: "help with internet"
date: 2010-04-05
forum: General Help
---

### Post by annasman05 on 2010-04-05
hey guys, i just recently installed ubuntu 9.10, and i'm having trouble connecting to the internet. ubuntu wont find my wireless network, and im wondering if it has something to do with a missing driver? any ideas? thanks everyone.

---

### Post by Iowan on 2010-04-05
Check (post if possible) **sudo lshw -C network**. That *should* show details about interfaces - and hopefully drivers.

---

### Post by warfacegod on 2010-04-05
Go to: System> Admin.> Hardware Drivers and see if there is a Recommended wireless driver in there that needs to be activated.

There is likely to be one for your video card there too.

---

### Post by gordintoronto on 2010-04-06
When I first tried Ubuntu, it took me a while to understand that Linux includes hundreds (thousands?) of drivers that "just work." However, there are a lot of wireless adapters which are not included. In the community docs there is a partial list of wireless adapters and whether they work "out of the box." [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

To find out what wireless adapter you have, open Accessories/Terminal and run the command:
lspci
This will produce around 20 lines of output, and your wireless adapter will be near the bottom. On my system, the line looks like:
03:07.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

The magic word is "ar2413" and my adapter works out of the box. To connect to my network, I right-clicked on the Network Manager icon, top-right, near the volume control. I selected "edit connections," clicked the wireless tab and "add" button, entered my SSID, encryption type and passphrase. It connected immediately.

If your wireless adapter doesn't work out of the box, it can be very annoying.

---

