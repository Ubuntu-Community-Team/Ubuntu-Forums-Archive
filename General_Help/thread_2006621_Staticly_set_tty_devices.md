---
title: "Staticly set tty devices?"
date: 2012-06-19
forum: General Help
---

### Post by jumping_snake on 2012-06-19
So, I'm not sure this can happen, but here's my current situation:

I have a Hylafax w/ Avantfax device that has 3 fax lines connected to it. I have 3 USB modems plugged into the device. Sometimes, when the device is restarted, the modems will initialize in a different order, changing their tty from say ttyACM0 to ttyACM1. I then have to go into Avantfax to change the modem settings around so that the correct lines are getting the correct emailed faxes.

I've been searching to see if there's a way to statically set the modems so that the same modem will always resolve to the same tty each time the server is rebooted. 

Would something like this work? ([http://www.hylafax.org/archive/2010-11/msg00141.php](http://www.hylafax.org/archive/2010-11/msg00141.php))
It seems like a weird/probably not working way to attempt it

I've also seen a function called setserial ([http://linux.about.com/library/cmd/blcmdl8_setserial.htm](http://linux.about.com/library/cmd/blcmdl8_setserial.htm))
This seems to be overkill

---

### Post by jumping_snake on 2012-06-21
Ok, from what I've been finding, it appears that I'll have to setup rules using udev in order to get this to work. Following this ([http://hackaday.com/2009/09/18/how-to-write-udev-rules/]("http://hackaday.com/2009/09/18/how-to-write-udev-rules/")), I've found this data from one of the modems:

```
 looking at device '/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/tty/ttyACM1':
    KERNEL=="ttyACM1"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0':
    KERNELS=="4-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="cdc_acm"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="02"
    ATTRS{bInterfaceSubClass}=="02"
    ATTRS{bInterfaceProtocol}=="01"
    ATTRS{modalias}=="usb:v0803p3095d0100dc02dsc00dp00ic02isc02ip01"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{bmCapabilities}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1a.1/usb4/4-2':
    KERNELS=="4-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="1965"
    ATTRS{idVendor}=="0803"
    ATTRS{idProduct}=="3095"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="02"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="2"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="4"
    ATTRS{devnum}=="8"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Conexant"
    ATTRS{product}=="USB Modem"
    ATTRS{serial}=="24680246"

  looking at parent device '/devices/pci0000:00/0000:00:1a.1/usb4':
    KERNELS=="usb4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="148"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="4"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.32-33-server uhci_hcd"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{serial}=="0000:00:1a.1"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1a.1':
    KERNELS=="0000:00:1a.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x2938"
    ATTRS{subsystem_vendor}=="0x1028"
    ATTRS{subsystem_device}=="0x020d"
    ATTRS{class}=="0x0c0300"
    ATTRS{irq}=="21"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{modalias}=="pci:v00008086d00002938sv00001028sd0000020Dbc0Csc03i00"
    ATTRS{numa_node}=="-1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

Currently, I'm going to test out rules today to see if I can get it to work, but if anybody has a better understanding of udev and wouldn't mind sharing what they think might work, please don't hesitate to post :)

---

### Post by jumping_snake on 2012-07-26
After doing some more searching, I found that what I was looking for exists, but not how I was expecting it: Using udev, I can find the ATTRS{serial} for each of my USB modems, but they all have the same serial number due to the fact that they're all the same brand/type of modem. (I'm not sure if that's the same for all external modems, but that's something that I might look up :) )

Therfore, I'm now wondering if I can find a different variable that doesn't change that I could use to create the udev rule. IRQ? Other?

Basically, once again if anybody knows anything, I'm willing to listen to any ideas :)

---

### Post by Cheesehead on 2012-07-26
Strange. Identical devices should have the same vendor, model, etc. numbers, but *not* the same serial number. That defeats the purpose of having serial numbers.

Are you sure you looked at all three, and not the same one three times?
Try [FONT="Courier New"]lsusb --vv[/FONT] to get a closer look at usb hardware.

---

### Post by jumping_snake on 2012-07-30
> **Cheesehead said:**
> Strange. Identical devices should have the same vendor, model, etc. numbers, but *not* the same serial number. That defeats the purpose of having serial numbers.

Are you sure you looked at all three, and not the same one three times?
Try [FONT="Courier New"]lsusb --vv[/FONT] to get a closer look at usb hardware.

Will do, and I'll report back as soon as I can.

---

### Post by jumping_snake on 2012-07-30
I'll attach the full output below, but here's the important info:

The 3 modems we want to use (especially for future projects like this) all have a serial of: 24680246. The single older modem doesn't have a serial, or a serial of 0.

I'm now beginning to think that I'll have to set modems like I was thinking, but then re-write each config for each modem every time the box reboots so that ttyACM0 always points and reports a specific phone number.



```
Bus 007 Device 002: ID 0803:3095 Zoom Telephonics, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0803 Zoom Telephonics, Inc.
  idProduct          0x3095 
  bcdDevice            1.00
  iManufacturer           1 Conexant
  iProduct                2 USB Modem
  iSerial                 3 24680246
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           73
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             128
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      CDC Header:
        bcdCDC               1.10
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x07
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Country Selection:
        iCountryCodeRelDate        4 04052004
        wCountryCode          0x4803
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           96
    bNumInterfaces          3
    bConfigurationValue     2
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             128
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      CDC Header:
        bcdCDC               1.10
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x07
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Country Selection:
        iCountryCodeRelDate        4 04052004
        wCountryCode          0x4803
Device Status:     0x0000
  (Bus Powered)
```

```
Bus 006 Device 005: ID 0803:3095 Zoom Telephonics, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0803 Zoom Telephonics, Inc.
  idProduct          0x3095 
  bcdDevice            1.00
  iManufacturer           1 Conexant
  iProduct                2 USB Modem
  iSerial                 3 24680246
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           73
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             128
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      CDC Header:
        bcdCDC               1.10
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x07
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Country Selection:
        iCountryCodeRelDate        4 04052004
        wCountryCode          0x4803
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           96
    bNumInterfaces          3
    bConfigurationValue     2
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             128
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      CDC Header:
        bcdCDC               1.10
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x07
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Country Selection:
        iCountryCodeRelDate        4 04052004
        wCountryCode          0x4803
Device Status:     0x0000
  (Bus Powered)
```

```
Bus 004 Device 003: ID 0803:3095 Zoom Telephonics, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0803 Zoom Telephonics, Inc.
  idProduct          0x3095 
  bcdDevice            1.00
  iManufacturer           1 Conexant
  iProduct                2 USB Modem
  iSerial                 3 24680246
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           73
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             128
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      CDC Header:
        bcdCDC               1.10
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x07
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Country Selection:
        iCountryCodeRelDate        4 04052004
        wCountryCode          0x4803
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           96
    bNumInterfaces          3
    bConfigurationValue     2
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             128
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      CDC Header:
        bcdCDC               1.10
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x07
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Country Selection:
        iCountryCodeRelDate        4 04052004
        wCountryCode          0x4803
Device Status:     0x0000
  (Bus Powered)
```

```
Bus 004 Device 002: ID 0572:1280 Conexant Systems (Rockwell), Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0572 Conexant Systems (Rockwell), Inc.
  idProduct          0x1280 
  bcdDevice            1.00
  iManufacturer           1 Conexant Systems, Inc.
  iProduct                2 USB ACF Modem
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           73
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          3 Configuration for ACF/HCF/HSF modem
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              260mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              4 Conexant USB interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              4 Conexant USB interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      CDC Header:
        bcdCDC               1.10
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x07
          sends break
          line coding and serial state
          get/set/clear comm features
      Country Selection:
        iCountryCodeRelDate        5 07141997
        wCountryCode          0x4803
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled
```

---

### Post by Cheesehead on 2012-07-30
Good grief, they sure do have similar serial numbers!
How obnoxious of the manufacturer!

I think you are on the right track with a udev rule. I wonder if udev will use the USB bus number as an attribute to tell them apart.

When booting your system, plan on a few extra seconds. Typically, the kernel will assign an interface to each device before udev loads...then udev will unassign and reassign each according to it's rules. All of these assignments/reassignments will be logged in /var/log/dmesg, and are easy to grep for if you need to troubleshoot. Connectivity will occur a few seconds later in the boot cycle than you may be used to.

---

### Post by jumping_snake on 2012-08-14
Ok, new development:

I purchased 4 new modems (2 of each): 

USRobotics: 
[http://www.amazon.com/USRobotics-USR5637-FaxModem-Windows-Linux/dp/B0013FDLM0](http://www.amazon.com/USRobotics-USR5637-FaxModem-Windows-Linux/dp/B0013FDLM0)

TRENDnet:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16825134008](http://www.newegg.com/Product/Product.aspx?Item=N82E16825134008)

Even these report the same serial(24680246). However, I can see each serial number written on each modem, and they're nothing like that number. For some reason, is Linux not able to grab the serial number correctly? Am I missing drivers or something? Please help! If I can, I'd like to avoid having to build a wheel that's already been created...

---

### Post by jumping_snake on 2012-08-14
Alright, I think I finally cracked it! I'm going to use the physical location of the modems along the USB hierarchy to get this solved. Therefore, here are the rules that I'm going to try:

75-persistent-modems.rules -
```
# Line 1
SUBSYSTEMS=="usb", KERNELS=="4-1:1.0", SYMLINK+="Modem01"

# Line 2
SUBSYSTEMS=="usb", KERNELS=="4-2:1.0", SYMLINK+="Modem02"

# Line 3
SUBSYSTEMS=="usb", KERNELS=="3-4.2:2.0", SYMLINK+="Modem03"

# Line 4
SUBSYSTEMS=="usb", KERNELS=="3-4.3:2.0", SYMLINK+="Modem04"

```

Now I just need to find an analog line I can use...

---

### Post by jumping_snake on 2012-08-21
Well, I was able to test and everything is working great!! 

It's strange that the serial number couldn't be grabbed by udevadm on any of the external usb modems I tried, but alas, I digress :)

---

