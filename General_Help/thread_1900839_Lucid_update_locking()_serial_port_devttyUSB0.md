---
title: "Lucid update locking(?) serial port /dev/ttyUSB0"
date: 2011-12-27
forum: General Help
---

### Post by rogermm on 2011-12-27
Hi all,

I would greatly appreciate any help/advice on the following:

A recent update (25.12.11) for Lucid 10.04.3 seems to have changed permissions or added a new locking mechanism for my serial port - /dev/ttyUSB0.

Prior to the update I was accessing a number of XBee to USB converters - one at a time - at this port. Unplugging one and plugging in another was no problem.  Each one was accessible from /dev/ttyUSB0. 

Following the update I am only able to access the first device connected.  Thereafter I am unable to connect to any subsequent device; even the same one if it is unplugged and re-plugged.  

To access another device, or the same one if it has been unplugged, I have to reboot the system.   


Output for ls -l /dev/ttyUSB0 is: 
crw-rw---- 1 root dialout 188, 0 2011-12-27 11:15 /dev/ttyUSB0 


The 25.12.11 update included the following:
Upgraded the following packages:
app-install-data-partner (12.10.04.4) to 12.10.04.5
libarchive1 (2.8.0-2) to 2.8.0-2ubuntu0.1
libgweather-common (2.30.0-0ubuntu1) to 2.30.0-0ubuntu1.1
libgweather1 (2.30.0-0ubuntu1) to 2.30.0-0ubuntu1.1
libjasper1 (1.900.1-7) to 1.900.1-7ubuntu0.10.04.1
linux-backports-modules-alsa-lucid-generic (2.6.32.36.42) to 2.6.32.37.43
linux-generic (2.6.32.36.42) to 2.6.32.37.43
linux-headers-generic (2.6.32.36.42) to 2.6.32.37.43
linux-image-generic (2.6.32.36.42) to 2.6.32.37.43
linux-libc-dev (2.6.32-36.79) to 2.6.32-37.81

Installed the following packages:
linux-backports-modules-alsa-2.6.32-37-generic (2.6.32-37.38)
linux-headers-2.6.32-37 (2.6.32-37.81)
linux-headers-2.6.32-37-generic (2.6.32-37.81)
linux-image-2.6.32-37-generic (2.6.32-37.81)


Thanks in advance.
rmm

---

### Post by Him on 2011-12-27
I believe I may be experiencing the same thing as you. If I boot up with a previous version of the kernel (2.6.32-36-generic) my device returns to working just as it did before, so try that for now. I'm not sure what's changed in the newer kernel, but I'm planning on looking into it soon.

In case it's helpful, here's the verbose lsusb output for my device, an old USB-UIRT using the "usb_uirt_raw" driver with LIRC:```
Bus 003 Device 004: ID 0403:f850 Future Technology Devices International, Ltd
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0403 Future Technology Devices International, Ltd
  idProduct          0xf850
  bcdDevice            6.00
  iManufacturer           1 FTDI
  iProduct                2 USB-UIRT
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2 USB-UIRT
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
Device Status:     0x0000
  (Bus Powered)
```

---

### Post by rogermm on 2011-12-28
Hi Him,

thanks very much for your reply.  Yes, the problem is definitely with 2.6.32-37-generic.  Using 2.6.32-36-generic also solves the problem for me.

My problems arise when connecting Sp*rkfun XBee Explorers - FTDI USB Serial converters.

Below is the output from dmesg | tail after:
a.) connecting XBee Explorer #1
b.) disconnecting XBee Explorer #1
c.) connecting XBee Explorer #2
d.) disconnecting XBee Explorer #2

```

//after connecting device #1
[   46.898126] USB Serial support registered for FTDI USB Serial Device
[   46.898282] ftdi_sio 3-1:1.0: FTDI USB Serial Device converter detected
[   46.898304] usb 3-1: Detected FT232RL
[   46.898306] usb 3-1: Number of endpoints 2
[   46.898308] usb 3-1: Endpoint 1 MaxPacketSize 64
[   46.898310] usb 3-1: Endpoint 2 MaxPacketSize 64
[   46.898311] usb 3-1: Setting MaxPacketSize 64
[   46.899423] usb 3-1: FTDI USB Serial Device converter now attached to ttyUSB0
[   46.899436] usbcore: registered new interface driver ftdi_sio
[   46.899437] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver

//after disconnecting device #1
[   46.898306] usb 3-1: Number of endpoints 2
[   46.898308] usb 3-1: Endpoint 1 MaxPacketSize 64
[   46.898310] usb 3-1: Endpoint 2 MaxPacketSize 64
[   46.898311] usb 3-1: Setting MaxPacketSize 64
[   46.899423] usb 3-1: FTDI USB Serial Device converter now attached to ttyUSB0
[   46.899436] usbcore: registered new interface driver ftdi_sio
[   46.899437] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver
[  102.328228] usb 3-1: USB disconnect, address 2
[  102.328598] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[  102.328638] ftdi_sio 3-1:1.0: device disconnected

//after connecting device #2
[  102.328638] ftdi_sio 3-1:1.0: device disconnected
[  214.528076] usb 3-1: new full speed USB device using uhci_hcd and address 3
[  214.721635] usb 3-1: configuration #1 chosen from 1 choice
[  214.729508] ftdi_sio 3-1:1.0: FTDI USB Serial Device converter detected
[  214.729566] usb 3-1: Detected FT232RL
[  214.729571] usb 3-1: Number of endpoints 2
[  214.729577] usb 3-1: Endpoint 1 MaxPacketSize 64
[  214.729582] usb 3-1: Endpoint 2 MaxPacketSize 64
[  214.729587] usb 3-1: Setting MaxPacketSize 64
[  214.730759] usb 3-1: FTDI USB Serial Device converter now attached to ttyUSB0

//after disconnecting device #2
[  214.729508] ftdi_sio 3-1:1.0: FTDI USB Serial Device converter detected
[  214.729566] usb 3-1: Detected FT232RL
[  214.729571] usb 3-1: Number of endpoints 2
[  214.729577] usb 3-1: Endpoint 1 MaxPacketSize 64
[  214.729582] usb 3-1: Endpoint 2 MaxPacketSize 64
[  214.729587] usb 3-1: Setting MaxPacketSize 64
[  214.730759] usb 3-1: FTDI USB Serial Device converter now attached to ttyUSB0
[  337.448100] usb 3-1: USB disconnect, address 3
[  337.448454] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[  337.448491] ftdi_sio 3-1:1.0: device disconnected

```And this is the verbose output for one of these devices using lsusb:

```

Bus 003 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0403 Future Technology Devices International, Ltd
  idProduct          0x6001 FT232 USB-Serial (UART) IC
  bcdDevice            6.00
  iManufacturer           1 FTDI
  iProduct                2 FT232R USB UART
  iSerial                 3 A900N7DV
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
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
      iInterface              2 FT232R USB UART
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
Device Status:     0x0000
  (Bus Powered)

```Hope this is helpful.  Unfortunately, this is not an area in which I have any competence.

---

