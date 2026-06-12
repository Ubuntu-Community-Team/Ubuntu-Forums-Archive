---
title: "FTDI-USB Issue on 12.04, Works on 9.04 / Windows"
date: 2012-10-09
forum: General Help
---

### Post by johnyo on 2012-10-09
I am having a problem using an FTDI-USB converter on 12.04; it works perfectly on my Ubuntu 9.04 and Windows. 

The FTDI USB converter shows up as ttyUSB0, but I am unable to connect to it! Can you see anything wrong here or point me in the right direction? I have all updates installed. 

$ uname -a
```

Linux ubuntu 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

$ dmesg
```

[28663.644817] usb 2-2.3: new full-speed USB device number 28 using uhci_hcd
[28663.834916] ftdi_sio 2-2.3:1.0: FTDI USB Serial Device converter detected
[28663.834938] usb 2-2.3: Detected FT232RL
[28663.834940] usb 2-2.3: Number of endpoints 2
[28663.834941] usb 2-2.3: Endpoint 1 MaxPacketSize 64
[28663.834942] usb 2-2.3: Endpoint 2 MaxPacketSize 64
[28663.834943] usb 2-2.3: Setting MaxPacketSize 64
[28663.846471] usb 2-2.3: FTDI USB Serial Device converter now attached to ttyUSB0

```

$ lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 016: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 028: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC

```

$ ls /dev/ttyUSB*
```

/dev/ttyUSB0

```

$ sudo screen /dev/ttyUSB0 9600
```

shows... a blank screen :(

```

Someone had a similar problem here: [http://ubuntuforums.org/showthread.php?t=1717311](http://ubuntuforums.org/showthread.php?t=1717311). However, they say they got one write and one read and then it fails. They fixed it by manually setting one of the lines, but I don't think I have the same problem because if I can successfully recognize the device as a USB-Serial converter, doesn't that mean it's all hooked up correctly?

Any help would be greatly appreciated!

---

### Post by johnyo on 2012-10-09
Optimistic Bump? Have tried several other computers which also all worked.

Is there any quirky configuration with USB / FTDI on Ubuntu 12.04? What might be the most likely cause of failure?

---

### Post by paciotti on 2013-02-01
Same problem here. No error messages, ttyUSB0 is present, but the serial interface don't work at all.

dmesg:
```
[   37.612136] usb 6-1: new full-speed USB device number 2 using uhci_hcd
[   37.874068] usbcore: registered new interface driver usbserial
[   37.874112] USB Serial support registered for generic
[   37.874263] usbcore: registered new interface driver usbserial_generic
[   37.874265] usbserial: USB Serial Driver core
[   37.895211] USB Serial support registered for FTDI USB Serial Device
[   37.895377] ftdi_sio 6-1:1.0: FTDI USB Serial Device converter detected
[   37.895458] usb 6-1: Detected FT232RL
[   37.895461] usb 6-1: Number of endpoints 2
[   37.895463] usb 6-1: Endpoint 1 MaxPacketSize 64
[   37.895465] usb 6-1: Endpoint 2 MaxPacketSize 64
[   37.895467] usb 6-1: Setting MaxPacketSize 64
[   37.898017] usb 6-1: FTDI USB Serial Device converter now attached to ttyUSB0
[   37.898051] usbcore: registered new interface driver ftdi_sio
[   37.898055] ftdi_sio: v1.6.0:USB FTDI Serial Converters Driver

```

The lines that differs from the dmesg on 10.04 (where the serial interface is running correctly) are:
```
[ 4052.359364] usb 2-1.6: new full speed USB device using ehci_hcd and address 3
[ 4052.457182] usb 2-1.6: configuration #1 chosen from 1 choice
...
[ 4052.547989] ftdi_sio 2-1.6:1.0: FTDI USB Serial Device converter detected
[ 4052.548133] usb 2-1.6: Detected FT232RL
[ 4052.548139] usb 2-1.6: Number of endpoints 2
[ 4052.548145] usb 2-1.6: Endpoint 1 MaxPacketSize 64
[ 4052.548151] usb 2-1.6: Endpoint 2 MaxPacketSize 64
[ 4052.548156] usb 2-1.6: Setting MaxPacketSize 64
[ 4052.548579] usb 2-1.6: FTDI USB Serial Device converter now attached to ttyUSB0
...
[ 4052.548668] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver


```

---

### Post by marlon_smith on 2013-12-10
Has anyone figured out this issue? I'm running Ubuntu 12.04 as well and I can receive data from an FTDI USB-Serial chip but I can't send to the chip.

---

