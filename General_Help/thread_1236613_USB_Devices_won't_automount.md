---
title: "USB Devices won't automount"
date: 2009-08-10
forum: General Help
---

### Post by djcrash1981 on 2009-08-10
Hi to all.

I'm getting this weird behavior after a kernel update through update-manager.

Before that my USB Thumbdrive and my cell phone where automounted by Ubuntu and showed on my desktop as another drive.

I'm using Intrepid Ibex (8.10)
**#uname -a**
Linux yavin4 2.6.27-14-generic #1 SMP Fri Jul 24 22:19:33 UTC 2009 i686 GNU/Linux

An here is a snippet of my syslog and messages log for when i connect my thumbdrive and my phone.

**#Messages**
Jul 30 16:01:47 yavin4 kernel: [  154.520020] usb 5-7: new high speed USB device using ehci_hcd and address 3
Jul 30 16:01:47 yavin4 kernel: [  154.660267] usb 5-7: configuration #1 chosen from 1 choice
Jul 30 16:01:47 yavin4 kernel: [  154.708594] Initializing USB Mass Storage driver...
Jul 30 16:01:47 yavin4 kernel: [  154.724937] scsi4 : SCSI emulation for USB Mass Storage devices
Jul 30 16:01:47 yavin4 kernel: [  154.746035] usbcore: registered new interface driver usb-storage
Jul 30 16:01:47 yavin4 kernel: [  154.746343] USB Mass Storage support registered.
Jul 30 16:01:47 yavin4 kernel: [  154.764060] usbcore: deregistering interface driver usb-storage
Jul 30 16:11:55 yavin4 kernel: [  762.092026] usb 3-2: new full speed USB device using uhci_hcd and address 2
Jul 30 16:11:55 yavin4 kernel: [  762.332026] usb 3-2: configuration #1 chosen from 1 choice
Jul 30 16:11:55 yavin4 kernel: [  762.371734] Initializing USB Mass Storage driver...
Jul 30 16:11:55 yavin4 kernel: [  762.394547] scsi5 : SCSI emulation for USB Mass Storage devices
Jul 30 16:11:55 yavin4 kernel: [  762.424237] scsi6 : SCSI emulation for USB Mass Storage devices
Jul 30 16:11:55 yavin4 kernel: [  762.436099] usbcore: registered new interface driver usb-storage
Jul 30 16:11:55 yavin4 kernel: [  762.436401] USB Mass Storage support registered.
Jul 30 16:11:55 yavin4 kernel: [  762.447339] usbcore: deregistering interface driver usb-storage

**#Syslog**
Jul 30 16:11:55 yavin4 kernel: [  762.092026] usb 3-2: new full speed USB device using uhci_hcd and address 2
Jul 30 16:11:55 yavin4 kernel: [  762.332026] usb 3-2: configuration #1 chosen from 1 choice
Jul 30 16:11:55 yavin4 kernel: [  762.371734] Initializing USB Mass Storage driver...
Jul 30 16:11:55 yavin4 kernel: [  762.394547] scsi5 : SCSI emulation for USB Mass Storage devices
Jul 30 16:11:55 yavin4 kernel: [  762.404765] usb-storage: device found at 3
Jul 30 16:11:55 yavin4 kernel: [  762.404771] usb-storage: waiting for device to settle before scanning
Jul 30 16:11:55 yavin4 kernel: [  762.424237] scsi6 : SCSI emulation for USB Mass Storage devices
Jul 30 16:11:55 yavin4 kernel: [  762.436099] usbcore: registered new interface driver usb-storage
Jul 30 16:11:55 yavin4 kernel: [  762.436401] USB Mass Storage support registered.
Jul 30 16:11:55 yavin4 kernel: [  762.436733] usb-storage: device found at 2
Jul 30 16:11:55 yavin4 kernel: [  762.436738] usb-storage: waiting for device to settle before scanning
Jul 30 16:11:55 yavin4 kernel: [  762.447339] usbcore: deregistering interface driver usb-storage
Jul 30 16:11:55 yavin4 pulseaudio[8685]: module-hal-detect.c: Error getting capability: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_13fe_1a00_5B6B0800D4B4_if0_scsi_host

And they are correctly detected
**# lsusb -v**
Bus 003 Device 002: ID 0421:04ed Nokia Mobile Phones 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0421 Nokia Mobile Phones
  idProduct          0x04ed 
  bcdDevice            1.00
  iManufacturer           1 Nokia
  iProduct                2 *Nokia N95*
  iSerial                 3 ***************
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 Bulk transfer method configuration
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              6 USB Mass Storage Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered

Bus 005 Device 003: ID 13fe:1a00 Kingston Technology Company Inc. 512MB/1GB Flash Drive
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x13fe Kingston Technology Company Inc.
  idProduct          0x1a00 512MB/1GB Flash Drive
  bcdDevice            1.00
  iManufacturer           1 Kingston
  iProduct                2 *DataTraveler 2.0*
  iSerial                 3 ***********
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
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
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
Device Status:     0x0000
  (Bus Powered)

I've already tried to put in the /etc/modules the usb_storage module, but it won't work still. It isn't loaded any way.

I don't know what else to do. I hope someone can show me some light in this problem.

Thanks

---

### Post by jerrrys on 2009-08-10
don't think i have had thumbdrive automount since 8.04.01; camera still automounts.  anyhow i found that in terminal  **lsusb** will bring it up everytime...

---

### Post by petegreenhorn on 2009-08-20
Hi djcrash1981, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/300394](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/300394)
this could be the answer (not the cure ) to your problem . Sorry i can't tell you it's being worked on as i don't know (i have same problem only in jaunty ).

---

