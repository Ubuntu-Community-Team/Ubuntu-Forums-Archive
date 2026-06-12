---
title: "Shimodul Miniplex-USB-AIS not working"
date: 2010-08-27
forum: General Help
---

### Post by bb75 on 2010-08-27
I own a Shipmodul Minipplex-AIS-USB. This is a NMEA data multiplexer for usage on board of boats. It basically is able to read from 4 NMEA inputs, collect that and send it to the PC using a serial to USB conversion. It connects at 38400 baud.
The device works nicely in Windows, or on my Mac. However, on Linux (Ubuntu 10.04) I cannot get it to do anything.
What I need to have is a device like /dev/ttyUSB1 to connect to. USB0 is my USB GPS device, which works nicely using the prolific drivers. this was automatically detected and all.

```
Bus 002 Device 005: ID 0403:fd49 Future Technology Devices International, Ltd 
Bus 002 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
```

```

$ lsusb -v -s002:005

Bus 002 Device 005: ID 0403:fd49 Future Technology Devices International, Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0403 Future Technology Devices International, Ltd
  idProduct          0xfd49 
  bcdDevice            4.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               90mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

```

> Aug 27 21:24:15 desktop kernel: [16468.849066] usb 2-2: new full speed USB device using uhci_hcd and address 6
Aug 27 21:24:15 desktop kernel: [16469.055147] usb 2-2: configuration #1 chosen from 1 choice


Any ideas more than welcome. Oh, I did try:
```
sudo modprobe usbserial vendor=0x0403 product=0xfd49
```
Didn't do anything....

---

### Post by bb75 on 2010-08-27
Got it!

Weirdly enough, this did it:

put in /etc/modprobe.d/usbserial :

options usbserial vendor=0x0403 product=0xfd49

---

### Post by littlechay on 2011-05-12
I have not had any luck with getting my shipmodule USB2 to talk to my netbook running 11.4. I have done all of the above, the device is recognised, shows up in lsusb, it is there as /dev/ttyUSB0.

When I do cat /dev/ttyUSBO all I get on screen are binary hieroglyphics when I would expect to see NMEA text. I'm close but just not quite there. 

Getting very much the same result with a Comar Systems AIS-Multi too, which also uses FTDI chipset.

I can use some other USB GPS etc without problems. a Garmin GPS 60 works fine and a BU353.

Any ideas and pointers to help me decode the hieroglyphics would be very welcome.

I'm running Raymarine instruments, ST 60+ series, ST 70 pilot controller, hoping to interface it all to OpenCPN on Linux. Got it all working on windows and Mac but would like to have it Open Source.

---

### Post by bb75 on 2011-05-19
Check the baudrate on the port and set it to 9600 baud or 4800 baud for a GPS USB module or 38k4 for an AIS.

P.S. you are close :). it is working!

---

### Post by Fliewaskip on 2012-03-17
The chipset ist a FTDI, so you need:

insmod ftdi_sio vendor=0x0403 product=0xfd49

The initial baudrate is 57600. (this prevents the mux from overloads)

---

