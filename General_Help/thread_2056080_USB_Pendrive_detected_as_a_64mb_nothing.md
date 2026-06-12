---
title: "USB Pendrive detected as a 64mb nothing"
date: 2012-09-10
forum: General Help
---

### Post by Epodx64 on 2012-09-10
I have an 8Gb USB Pendrive that recently stopped working on all computers I tried it on a Cent OS install Windows XP & Kubuntu 
here's what lsusb  gives
```
Bus 001 Device 004: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK
```then sudo lsusb -v
```
Bus 001 Device 004: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x090c Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.)
  idProduct          0x1000 64MB QDI U2 DISK
  bcdDevice           11.00
  iManufacturer           1 SMI Corporation
  iProduct                2 USB DISK
  iSerial                 3 AA200905250000000182
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
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      
Device Status:     0x0000
  (Bus Powered)

```QD1 U2 Disk is waiting it's showing up as all my other usb drives work fine and it post like that in all the usb ports I don't any idea's?

---

### Post by Epodx64 on 2012-09-10
Well I managed to get it to mount by getting the sudo blck uuid 
sudo mkfs  /media/usb8
sudo mount -U <UUID> 
cd /media/usb8
ls shows theres a live cd installed on it which I don't entirely understand

---

