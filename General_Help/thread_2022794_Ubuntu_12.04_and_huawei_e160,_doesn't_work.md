---
title: "Ubuntu 12.04 and huawei e160, doesn't work"
date: 2012-07-11
forum: General Help
---

### Post by h2opolomatti on 2012-07-11
Hello,

I've got problem with huawei e160 on ubuntu 12.04. 
When i plug in modem to lapton (Acer aspire), network manager doesnt discover the modem so i'cant create connection in NM and connect to internet. I've tried lot of ways looked up in internet with no results. Also i noticed that when i plug in modem often ubuntu freezes for a while. 

ateusz@mateusz-Aspire-5738:~$ sudo usb_modeswitch -v 0x12d1 -p 0x1003 -H 
[sudo] password for mateusz: 

aLooking for default devices ... 
   found matching product ID 
   adding device 
 Found device in default mode, class or configuration (1) 
Accessing device 002 on bus 001 ... 
Getting the current device configuration ... 
 OK, got current device configuration (1) 
Using first interface: 0x00 
Using endpoints 0x01 (out) and 0x82 (in) 
Not a storage device, skipping SCSI inquiry 

USB description data (for identification) 
------------------------- 
Manufacturer: HUAWEI Technology 
     Product: HUAWEI Mobile 
  Serial No.: not provided 
------------------------- 
Sending Huawei control message ... 
 OK, Huawei control message sent 
-> Run lsusb to note any changes. Bye.


Dmesg 

[  521.480062] usb 1-4: reset high-speed USB device number 4 using ehci_hcd 
[  521.617792] option 1-4:1.1: GSM modem (1-port) converter detected 
[  521.617945] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB0 
[  521.618062] option 1-4:1.0: GSM modem (1-port) converter detected 
[  521.618232] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB1 
[  530.840276] option: option_instat_callback: error -108 
[  530.840455] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1 
[  530.840484] option 1-4:1.0: device disconnected 
[  537.680378] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0 
[  537.680398] option 1-4:1.1: device disconnected 
[  537.792088] usb 1-4: reset high-speed USB device number 4 using ehci_hcd 
[  537.929549] option 1-4:1.1: GSM modem (1-port) converter detected 
[  537.929702] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB0 
[  537.929818] option 1-4:1.0: GSM modem (1-port) converter detected 
[  537.929993] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB1 
[  547.224294] option: option_instat_callback: error -108 
[  547.224470] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1 
[  547.224511] option 1-4:1.0: device disconnected 
[  556.988066] tty_ldisc_hangup: waiting (usb-storage) for ttyUSB0 took too long, but we keep waiting... 
[  558.990663] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0 
[  558.990698] option 1-4:1.1: device disconnected 
[  559.100068] usb 1-4: reset high-speed USB device number 4 using ehci_hcd 
[  559.241293] option 1-4:1.1: GSM modem (1-port) converter detected 
[  559.241446] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB0 
[  559.241565] option 1-4:1.0: GSM modem (1-port) converter detected 
[  559.241739] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB1 
[  568.728283] option: option_instat_callback: error -108 
[  568.728466] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1 
[  568.728496] option 1-4:1.0: device disconnected 

lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 003: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314] 
Bus 005 Device 002: ID 09da:c20a A4 Tech Co., Ltd 
Bus 001 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem


i would be greatefull if you can help me, i must work on Windows - you know what i mean :/

---

