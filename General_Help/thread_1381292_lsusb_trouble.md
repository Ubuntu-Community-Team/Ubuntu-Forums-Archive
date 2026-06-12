---
title: "lsusb trouble"
date: 2010-01-14
forum: General Help
---

### Post by mw2000 on 2010-01-14
Hello,

I am new in this forum and hope to get some help which I could not get from Google.

I swichted over to linux (kubuntu 9.10) half a year ago and I am quiet happy so far. Now i am trying to programm an appliction for a selfmade USB device. The application and the device are working fine under WinXP, so I know the device is OK. The device uses the USB-HID Protokoll.

Now I started with using libhid and got some errors and I try to figure out what happens. To open the pipe, I need to analyze the 'HID Device Descriptor'.

lsusb should bring the answer:

**sudo lsusb -d 046d:c508 -vvv  (for testing my trackball)**

```
Bus 001 Device 008: ID 046d:c508 Logitech, Inc. Cordless Trackball
Device Descriptor:                                                
  bLength                18                                       
  bDescriptorType         1                                       
  bcdUSB               1.10                                       
  bDeviceClass            0 (Defined at Interface level)          
  bDeviceSubClass         0                                       
  bDeviceProtocol         0                                       
  bMaxPacketSize0         8                                       
  idVendor           0x046d Logitech, Inc.                        
  idProduct          0xc508 Cordless Trackball                    
  bcdDevice           15.00                                       
  iManufacturer           1 Logitech                              
  iProduct                2 USB Receiver                          
  iSerial                 0                                       
  bNumConfigurations      1                                       
  Configuration Descriptor:                                       
    bLength                 9                                     
    bDescriptorType         2                                     
    wTotalLength           34                                     
    bNumInterfaces          1                                     
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               50mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0
      ** UNRECOGNIZED:  09 21 10 01 00 01 22 4c 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)
```Why I cant see the HID-Descriptor (** UNRECOGNIZED:  09 21 10 01 00 01 22 4c 00) for none of my HID devices.
I wondering if there is an other bug may be in my system.

Any help?

mw2000

---

