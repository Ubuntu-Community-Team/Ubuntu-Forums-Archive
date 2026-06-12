---
title: "Copy files from device only visible using lsusb"
date: 2012-09-11
forum: General Help
---

### Post by Apop on 2012-09-11
I've accidentally deleted my files on a GPS watch that I've only been able to access using the crappy software that I downloaded from the watch's website.  Is there any way to access this device that I can only view with lsusb? If so, can I copy EVERYTHING, including files marked as available(I.e. the files I recently deleted)?  Thanks!

---

### Post by Apop on 2012-09-11
Here is the info from lsusb -v: 

```
Bus 003 Device 006: ID 10c4:ea61 Cygnal Integrated Products, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x10c4 Cygnal Integrated Products, Inc.
  idProduct          0xea61 
  bcdDevice            1.00
  iManufacturer           1 Silicon Labs
  iProduct                2 CP2102 USB to UART Bridge Controller
  iSerial                 3 8887
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
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              2 CP2102 USB to UART Bridge Controller
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
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

```

---

### Post by cortman on 2012-09-11
To copy files you must mount a partition on the device. You can't copy with lsusb.
What is the output of 

```
sudo fdisk -l
```

and

```
df
```

---

### Post by steeldriver on 2012-09-11
looks like it is a serial device though?

---

