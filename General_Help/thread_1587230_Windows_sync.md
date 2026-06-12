---
title: "Windows sync"
date: 2010-10-03
forum: General Help
---

### Post by cowboy7305 on 2010-10-03
I have a gps unit that i can only look at its files using window sync, the gps does not show up on ubuntu 10.04 
is there ay way i can look at the files on this gps unit other that having to use windows 7

---

### Post by madverb on 2010-10-03
Please put more information in the title for starters.

What brand and model is the GPS? Have you done any research via google or the like? Does the GPS do anything when connected to Ubuntu? Information is helpful.

---

### Post by cowboy7305 on 2010-10-03
The model of gps is Tevion gps4301
when i plug it up to ubuntu 10.04 it does not show up 
have looked at google and i get totaly lost with info all for windows with hacked units ,and i have no idea what windows sync does bar looking at the files ,

---

### Post by btindie on 2010-10-03
When you connect your GPS to Ubuntu run ```
sudo dmesg | tail -n 50
``` and post the result.

---

### Post by cowboy7305 on 2010-10-03
[   16.008085]  domain 0: span 0-1 level MC
[   16.008088]   groups: 1 0
[   17.165255] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   17.165259] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   17.165451] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   18.035708] CPU0 attaching NULL sched-domain.
[   18.035714] CPU1 attaching NULL sched-domain.
[   18.052563] CPU0 attaching sched-domain:
[   18.052567]  domain 0: span 0-1 level MC
[   18.052569]   groups: 0 1
[   18.052575] CPU1 attaching sched-domain:
[   18.052577]  domain 0: span 0-1 level MC
[   18.052580]   groups: 1 0
[   27.952510] eth0: no IPv6 routers present
[   68.612029] usb 7-2: new full speed USB device using uhci_hcd and address 3
[   68.751509] usb 7-2: not running at top speed; connect to a high speed hub
[   68.774668] usb 7-2: configuration #1 chosen from 1 choice
[   68.833454] usbcore: registered new interface driver usbserial
[   68.833683] USB Serial support registered for generic
[   68.833742] usbcore: registered new interface driver usbserial_generic
[   68.833744] usbserial: USB Serial Driver core
[   68.842623] USB Serial support registered for PocketPC PDA
[   68.842681] ipaq 7-2:1.0: PocketPC PDA converter detected
[   68.844655] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[   68.844680] usbcore: registered new interface driver ipaq
[   68.844682] ipaq: v0.5:USB PocketPC PDA driver
[   84.472057] usb 7-2: USB disconnect, address 3
[   84.472330] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[   84.472358] ipaq 7-2:1.0: device disconnected
[   87.936022] usb 7-2: new full speed USB device using uhci_hcd and address 4
[   88.135978] usb 7-2: not running at top speed; connect to a high speed hub
[   88.158128] usb 7-2: configuration #1 chosen from 1 choice
[   88.162069] ipaq 7-2:1.0: PocketPC PDA converter detected
[   88.164894] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[   95.384060] usb 7-2: USB disconnect, address 4
[   95.384325] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[   95.384352] ipaq 7-2:1.0: device disconnected
[   98.600045] usb 7-2: new full speed USB device using uhci_hcd and address 5
[   98.739322] usb 7-2: not running at top speed; connect to a high speed hub
[   98.762476] usb 7-2: configuration #1 chosen from 1 choice
[   98.767697] ipaq 7-2:1.0: PocketPC PDA converter detected
[   98.769950] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[  105.800053] usb 7-2: USB disconnect, address 5
[  105.800318] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[  105.800346] ipaq 7-2:1.0: device disconnected
[  109.264027] usb 7-2: new full speed USB device using uhci_hcd and address 6
[  109.399677] usb 7-2: not running at top speed; connect to a high speed hub
[  109.421824] usb 7-2: configuration #1 chosen from 1 choice
[  109.425767] ipaq 7-2:1.0: PocketPC PDA converter detected
[  109.427940] usb 7-2: PocketPC PDA converter now attached to ttyUS

---

### Post by btindie on 2010-10-03
It's detected your GPS (PocketPC PDA) and is connected to ttyUSB0 which is a serial port. I think those things generally use MS ActiveSync. Take a look at [this]("http://knowledgeworks.wordpress.com/2008/03/11/activesync-alternative-for-linux/") and [this]("http://www.modaco.com/content/i9x0-omnia-http-omnia-modaco-com/276325/active-sync-and-linux-ubuntu/"), it may point you in the right direction.
 
Have you tried enabling Mass Storage mode on your GPS to make it appear as an SD card??

---

### Post by cowboy7305 on 2010-10-03
I have looked at activ sync and i have no idea what it does i cal see the files on the gps using in ubut can not fo any thing with them 
and the gps does not show up on ubuntu ,but as you say ubuntu knows its therebut will not show it

---

