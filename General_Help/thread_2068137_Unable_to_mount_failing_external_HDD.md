---
title: "Unable to mount failing external HDD"
date: 2012-10-08
forum: General Help
---

### Post by Sagasardiin on 2012-10-08
I have a 1 Tb external hdd which is failing. When connected to a pc it makes the clicking noise for a while. 
Hdd wont show up on gparted nor in Testdisk.
Force mounting with sudo mount and sudo ntfs-3g won't work either, I presume because i dont know the partion label or something something ... 

Only data about the device i got was with  lsusb

> Bus 002 Device 010: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x152d JMicron Technology Corp. / JMicron USA Technology Corp.
  idProduct          0x2329 JM20329 SATA Bridge
  bcdDevice            0.00
  iManufacturer          10 0123456
  iProduct               11 Storagebird 35EV821
  iSerial                 3 000000000177
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 USB Mass Storage
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              6 MSC Bulk-Only Transfer
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered
Is there a way to mount the device and recovery any data ?

---

### Post by Sagasardiin on 2012-10-09
Could it make a difference if I pluged the hdd directly into a pc ?

---

### Post by Crafty Kisses on 2012-10-09
Clicking noise of a HD usually is a sign of drive failure, it could be the drive itself, what are the results of 
```
nano /etc/fstab
```

---

### Post by Mark Phelps on 2012-10-09
IF it makes clicking sounds for a few seconds and then goes quiet, touch the drive to see if it is still running.  I've had this happen, and when it did, the drive shut down.  If that happens, the drive has a serious hardware fault and, apart from sending it to a recovery service and paying LOTS of money, it is not recoverable.

However, if it is still running after the clicking, if the drive was formatted using MS Windows filesystem(s), it may still be recoverable.

Need to get back to us on this.

---

