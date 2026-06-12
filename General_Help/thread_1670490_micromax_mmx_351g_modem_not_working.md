---
title: "micromax mmx 351g modem not working"
date: 2011-01-19
forum: General Help
---

### Post by ManishSR on 2011-01-19
i followed exact same steps as described here [http://manish2dream.blogspot.com/2010/08/micromax-mmx-300g-modem-bsnl-3g-modem.html](http://manish2dream.blogspot.com/2010/08/micromax-mmx-300g-modem-bsnl-3g-modem.html)
but i am getting
> 
 sudo usb_modeswitch
 ! PLEASE REPORT NEW CONFIGURATIONS !
and 

> 
 sudo wvdial
 i forgot what aws the output, but it was something like cant find modem.
then i tried sakis3g
it also failed.

but now ubuntu automatically detected the usb modem and i am connected to the internet.
but when i restart ubuntu, it does not seem to  auto recognize the modem. but when execute sakis3g, after few mins, ubuntu recognizes and i am connected to the internet.

dmesg output (now)
> 
[  120.723176] usb 1-3: USB disconnect, address 2
[  121.088026] usb 1-3: new high speed USB device using ehci_hcd and address 4
[  121.885259] scsi7 : usb-storage 1-3:1.5
[  122.909608] scsi 7:0:0:0: Direct-Access     USBModem Disk             2.31 PQ: 0 ANSI: 2
[  122.913522] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  122.933101] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[  143.103007] usbcore: registered new interface driver usbserial
[  143.103053] USB Serial support registered for generic
[  143.105958] usbcore: registered new interface driver usbserial_generic
[  143.105965] usbserial: USB Serial Driver core
[  143.123752] USB Serial support registered for GSM modem (1-port)
[  143.126642] usbcore: registered new interface driver option
[  143.126648] option: v0.7.2:USB Driver for GSM modems
[  143.185867] option 1-3:1.0: GSM modem (1-port) converter detected
[  143.188962] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB0
[  143.189023] option 1-3:1.1: GSM modem (1-port) converter detected
[  143.189737] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB1
[  143.189785] option 1-3:1.2: GSM modem (1-port) converter detected
[  143.189873] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB2
[  143.189912] option 1-3:1.3: GSM modem (1-port) converter detected
[  143.189999] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB3
[  143.190037] option 1-3:1.4: GSM modem (1-port) converter detected
[  143.190147] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB4
[  342.935166] PPP BSD Compression module registered
[  342.973608] PPP Deflate Compression module registered
[  450.601251] dumpcap uses obsolete (PF_INET,SOCK_PACKET)
> 
lsusb
Bus 003 Device 002: ID 04f3:0230 Elan Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1c9e:9607  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
is there any less frustrating method to connect to internet ?
how to setup my usb modem, so it get recognized as soon as i plug it in.

ps: i dont see any network traffic in system moniter applet

---

