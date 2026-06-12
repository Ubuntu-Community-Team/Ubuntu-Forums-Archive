---
title: "Hardware problems (Logitech Media Desktop &amp; F5D7050 WiFi)"
date: 2010-04-29
forum: General Help
---

### Post by shade82000 on 2010-04-29
Hi all...
 
I've been using 9.10 for a while and had no real problems with Ubuntu in general, not until I installed this release. I've been waiting for 10.04 to become available, but now it won't work with some of my hardware.
 
 
 
First off, I have an SiS163u WLAN built into my PC - 9.10 would see the hardware but it didn't ever work, so I used my old Belkin F5D7050 USB adapter and that worked straight away. Since installing 10.04 the SiS is not even listed when I do a lsusb and the F5D7050 is shown in lsusb but no wlan device is shown in the GUI or ifconfig, so I cant connect to any networks.
 
 
 
Second, I have a Logitech DiNovo keyboard / mouse / media pad combo (which all connect using a single Logitech USB BT adapter). Although the extended features never worked in 9.10, it functioned perfectly as a standard keyb / mouse, but none of the 3 devices work at all in 10.04. I think the BT adapter is being seen because if I press any keys or move the mouse I get this:
 
[IMG]http://i439.photobucket.com/albums/qq119/shade82000/Screenshot-Mouse.png[/IMG]
 
No matter what I click on, nothing happens and another dialog pops up if it is moved again.
 
Any help with these two problems would be greatly appreciated, otherwise I'm gonna have to put 9.10 back on :( but at least 9.10 supports more of my hardware than Win 7 :)
 
 
Here is my lsusb output (ignore the '0425:0101 Motorola' - that's the other wireless keyboard I used)
 
Bus 005 Device 005: ID 046d:c709 Logitech, Inc. BT Mini-Receiver (HCI mode)
Bus 005 Device 004: ID 046d:c70c Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 005 Device 003: ID 046d:c70b Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 005 Device 002: ID 046d:0b02 Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0425:0101 Motorola Semiconductors HK, Ltd G-Tech Wireless Mouse & Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 001 Device 005: ID 0bf8:100f Fujitsu Siemens Computers 
Bus 001 Device 004: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by K1mp3 on 2010-05-03
same problem here, have the same mouse plus cordless keyboard...

Bus 004 Device 005: ID 046d:c709 Logitech, Inc. BT Mini-Receiver (HCI mode)
Bus 004 Device 004: ID 046d:c70a Logitech, Inc. MX5000 Cordless Desktop
Bus 004 Device 003: ID 046d:c70e Logitech, Inc. MX1000 Bluetooth Laser Mouse
Bus 004 Device 002: ID 046d:0b02 Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 05d5:6781 Super Gate Technology Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 04b3:3107 IBM Corp. ThinkPad 800dpi Optical Travel Mouse
Bus 001 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 001 Device 004: ID 0424:2602 Standard Microsystems Corp. 
Bus 001 Device 003: ID 0424:2502 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by K1mp3 on 2010-05-03
I found a workaround for Logitech from this bug report [https://bugs.launchpad.net/ubuntu/+s...ez/+bug/550288]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288")

change a line in /lib/udev/rules.d/70-hid2hci.rules
 from
 # Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d",  ATTRS{idProduct}=="c70[345abce]|c71[34bc]",  \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
 

to


 KERNEL=="hidraw*", ATTRS{idVendor}=="046d",  ATTRS{idProduct}=="c70[345abce]|c71[34bc]",  \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"

---

### Post by dino99 on 2010-05-03
some threads already about dinovo on this forum, with solutions

---

### Post by shade82000 on 2010-05-04
That's simply awesome.  Thank you bery much for pointing me in the right direction!  I haven't tried it but the hardware and symptoms are exactly the same as suggested in the linked post above, so I can only assume it will work and thank you all in advance!

---

### Post by shade82000 on 2010-05-04
Now the keyboard issues are probably solved, I wanted to ask for some technical help with the Belkin F5D7050 USB WiFi stick:

I have been reading in various Ubuntu posts that the problem is more than likely with the lack of RT2570 USB chipset drivers in 10.04.

Seems like it could be a relatively easy fix because I can see the RT2570 driver package in the package manager and have D/L & installed them.

The thing is, it just drops some files in a folder (/usr/share/....?) and expects me to compile them.

Anybody got any idea how I would go about this?

I read something about recompiling the kernel to include the RT2570 drivers.  Although I understand the principle of how and why I need to do this, I have no idea where to start with the command line.

A list of commands would be very helpful :~)

---

