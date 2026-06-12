---
title: "Cant see HTC EVO 4G LTE in Ubuntu 12.04"
date: 2012-06-10
forum: General Help
---

### Post by DeusExM1 on 2012-06-10
Hi everyone,

I am trying to connect my HTC EVO 4G LTE to ubuntu 12.04, but the device wont come up. I want to download some music to my phone from my PC, and install PDAnet (cant do it through the phone). 

Anyone know why the phone may not be showing up?

Thanks in advance for any help you may provide.

---

### Post by DeusExM1 on 2012-06-11
bump

---

### Post by odsus1 on 2012-06-17
Me too!

---

### Post by odsus1 on 2012-06-19
Can't see it on 12.04 (regular and xfce), xubuntu 11.04 or bodhi. I can connect the pc through the phones internet and vice versa, I just cant see it in a file manger, windows 8 (same machine as bodhi) sees it just fine.  Also, I have lost the ability to see an iphone, I don't know if that is related but i suspect so, no other problems with usb media

---

### Post by cjennn on 2012-07-19
Hello Linux community... I just bought an HTC Explorer and nothing happens when I plug it into the computer running on Ubuntu. I want to put some podcasts on it and also use it as a modem. I'm keen to hear some solutions, but I'm not very good at computers, so I'm looking for very basic instructions! Thanks all!

---

### Post by odsus1 on 2012-07-21
Still having this issue, lsusb output shows the device, all mpt packages are installed I even went as far as to install android sdk packages (I don't know what I thought that would accomplish). I contacted HTC (to no avail, they basically said use windows) 
Can I just create a mount point and point it at the usb port that the device is connected to?  
Output from lsusb (xubuntu 12.04 machine)

odsus1@odsus1-s5-1014:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge
Bus 001 Device 005: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
***Bus 001 Device 020: ID 0bb4:0ca8 High Tech Computer Corp. ***
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser

Any help would be appreciated
Odie

---

