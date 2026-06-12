---
title: "Help to connect SE k500i with usb cable"
date: 2009-09-13
forum: General Help
---

### Post by vvp86 on 2009-09-13
I have SonyEricsson k500i. And usb cable. I want to connect it to my pc to down/up-load to it. 
That's dmesg when the cable is connected:

[ 1042.188015] usb 5-1: new full speed USB device using uhci_hcd and address 3
[ 1042.347449] usb 5-1: configuration #1 chosen from 1 choice
[ 1042.350626] pl2303 5-1:1.0: pl2303 converter detected
[ 1042.363336] usb 5-1: pl2303 converter now attached to ttyUSB0

And that's lsusb string:

Bus 005 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

When i connect/disconnect the phone to the cable nothing happens.

Thank you.

UPD: In ObexTool i can see phone folders(Pictures, SOunds, etc) but i can't see any files. When i try to upload files error happens : Please check your permissions.

---

### Post by harrismh777 on 2009-09-13
> **vvp86 said:**
> 
[ 1042.188015] usb 5-1: new full speed USB device using uhci_hcd and address 3
[ 1042.347449] usb 5-1: configuration #1 chosen from 1 choice
[ 1042.350626] pl2303 5-1:1.0: pl2303 converter detected
[ 1042.363336] usb 5-1: pl2303 converter now attached to ttyUSB0



The messages are telling you that the kernel knows your pl2303 as serial device  ttyUSB0. 

The pl2303 is a fairly common usb | serial adapter (often used in usb pigtails) that converts a standard usb port to a (9 pin) serial port. 

You will need to configure your software to be able to use the device ttyUSB0.  ttyUSB0 is the kernel's physical access to the pl2303 hardware you plugged in.   Looks like the hardware connection is good... now you just need to get the software connection made.

---

### Post by vvp86 on 2009-09-13
Do you know any software which can help me?
Could i use obexfs and obexftp. And how do i use it f i could?
Thank you

---

