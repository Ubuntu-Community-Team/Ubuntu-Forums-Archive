---
title: "obtaining permission to install wireless driver"
date: 2010-10-07
forum: General Help
---

### Post by tony044 on 2010-10-07
[B]I have downloaded a driver for my D-LINK WIRELESS N NANO USB ADAPTER DWA-131, but everytime I try to install I get the message cannot change permissions. I am using WINE as it is a Windows7 driver. Any help gratefully received.
MSI U135X Notebook
RAM:1gb
HDD: 250gb
OP: LINUX UBUNTU 10.04 LTS
RF: 802.11b/g/n
Tony 044 [/B] :guitar:

---

### Post by realzippy on 2010-10-07
1.You cannot install a windows driver with wine in linux.
2.D-Link DWA-131 Nano USB Wireless N adapter (USB dongle) is using RealTek 8192SU chip,this chip does work on Kernel 2.6.33. That is, this chip may work on Ubuntu 10.10 or later,or you install a newer kernel.

---

### Post by coffeecat on 2010-10-07
> **tony044 said:**
> **I am using WINE as it is a Windows7 driver.**

I don't think that's going to work. To use a Windows driver you need to use ndiswrapper. The community documentation page...

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB)

... isn't much help for your card. Install the package ndisgtk which will install all the ndiswrapper bits. I've never had to use this myself, but I believe the ndisgtk GUI frontend does just about everything for you. Post back if you have problems and someone will be able to help.

**edit:** realzippy posted just seconds before me. From what realzippy says, it seems that your card may work with the inbuilt driver in 10.10/Maverick which will be released in a few days. Consider upgrading or reinstalling with Maverick if ndisgtk doesn't do the job.

---

