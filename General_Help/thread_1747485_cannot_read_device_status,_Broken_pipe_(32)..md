---
title: "cannot read device status, Broken pipe (32)."
date: 2011-05-02
forum: General Help
---

### Post by phil128 on 2011-05-02
Hi all.

I'm developing a driver atm. The driver I'm developing is for a special chip (connects via USB) on my motherboard that currently only works with Windows. When I connect my netbook to the device and I run lsusb -vv this is what I get.

```

      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      57
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN <-------- [1]
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
cannot read device status, Broken pipe (32)

```

The chip I'm developing couldn't just have a single IN endpointaddress [1], as the chip communicates back to the host, so it should have another endpoint OUT. 

The following error:

cannot read device status, Broken pipe (32)

Seems to happen when its trying to read the next endpointaddress the OUT.

Thanks

---

