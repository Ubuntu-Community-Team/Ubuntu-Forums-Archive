---
title: "Resident flash"
date: 2010-11-29
forum: General Help
---

### Post by cowboy7305 on 2010-11-29
I have a gps unit and i want to look at the files on its drive ,in windows it uses some thing like windows synk or some thing like that 
and it also shows up as a drive on windows computer
when i plug unit into ubuntu it does not show up as a drive its just not there ,is there any way that ubuntu can read this unit ,i know or think it is formatted to FAT

---

### Post by lykeion on 2010-11-29
Need more info to give you some help, like
1) what is the name of the GPS unit?
2) how do you connect it? USB/Serial-to-USB/?

unplug your unit and start a terminal (Applications > Accessories > Terminal)
3a) plug in your unit and enter this command and paste the output here:```
dmesg | tail
```
3b) enter this command and paste the output here:```
lsusb
```

---

### Post by cowboy7305 on 2010-11-30
[  275.176019] usb 7-1: new full speed USB device using uhci_hcd and address 3
[  275.398029] usbcore: registered new interface driver usbserial
[  275.398043] USB Serial support registered for generic
[  275.398072] usbcore: registered new interface driver usbserial_generic
[  275.398074] usbserial: USB Serial Driver core
[  275.452387] USB Serial support registered for PocketPC PDA
[  275.452452] ipaq 7-1:1.0: PocketPC PDA converter detected
[  275.453666] usb 7-1: PocketPC PDA converter now attached to ttyUSB0
[  275.453689] usbcore: registered new interface driver ipaq
[  275.453691] ipaq: v1.0:USB PocketPC PDA driver

---

### Post by cowboy7305 on 2010-11-30
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by lykeion on 2010-11-30
Is it a HP iPAQ PDA? If so try to search this forum with the name of your device. 
These are some links I found that might help:
[https://help.ubuntu.com/community/HP4150iPaqHowto](https://help.ubuntu.com/community/HP4150iPaqHowto)
[https://help.ubuntu.com/community/PortableDevices/WindowsMobile](https://help.ubuntu.com/community/PortableDevices/WindowsMobile)
[http://www.synce.org/moin/SynceInstallation/Ubuntu](http://www.synce.org/moin/SynceInstallation/Ubuntu)

---

### Post by cowboy7305 on 2010-12-02
no its a binatone x350 gps unit

---

### Post by lykeion on 2010-12-03
According to this: [http://old.nabble.com/Track-files-from-Binatone-x350-td21206042.html#a21206042](http://old.nabble.com/Track-files-from-Binatone-x350-td21206042.html#a21206042), the unit runs WindowsCE 5, so the links about Windows Mobile and SynCE above should be helpful.

---

