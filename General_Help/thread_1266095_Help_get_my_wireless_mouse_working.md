---
title: "Help get my wireless mouse working"
date: 2009-09-14
forum: General Help
---

### Post by HolyShnikes on 2009-09-14
I havent had linux on my computer for over a year now.  I use to have kubuntu, and also Suse, but I have heard so many great things about Ubuntu that I finally decided to give it a try (ver. 9.04).  

Here is my problem though, I have a wireless mouse that after I log in will randomly stop responding.  The keyboard will work fine, but the mouse is not responsive at all.  Sometimes its 10 minutes after I log in, sometimes its 30 seconds.  Its really frustrating to try and learn a new system with only a keyboard.  It also did this on the Live CD before I installed.  I thought it was a problem with the CD not Ubuntu.  I did install using Wubi in windows Vista.  

I have tried reseting the connection of the signal several times.  When I do, it connects fine, but there is still no movment or clicking on my mouse.  I also tried reseting X server.  The only way to get rid of it is to shut down the computer and restart it.  But this is only temporary as it stops working again later.  

If anyone can help me out with this I would greatly appreciate it.  Thanks.

---

### Post by P4man on 2009-09-14
what mouse are you using? IT sounds like a problem with USB.
A few things you can try:
-disable USB legacy support in your bios if you don't have a USB keyboard.
-Try a different USB port for the receiver
-open a terminal (with keyboard: alt+F2 and then type "gnome-terminal") and type:
```

sudo lsusb -v >usbinfo.txt
```

attach or copy/paste the contents of usbinfo.txt to a post here
Do the same for:

```
dmesg >log.txt
```

---

### Post by HolyShnikes on 2009-09-14
> **P4man said:**
> what mouse are you using? IT sounds like a problem with USB.
A few things you can try:
-disable USB legacy support in your bios if you don't have a USB keyboard.
-Try a different USB port for the receiver
-open a terminal (with keyboard: alt+F2 and then type "gnome-terminal") and type:
```

sudo lsusb -v >usbinfo.txt
```

attach or copy/paste the contents of usbinfo.txt to a post here
Do the same for:

```
dmesg >log.txt
```

Thanks, I will try that when I get home and post it.  Hopefully it will help.

I think I am using a microsoft wireless mouse and keyboard set.  I can't remember off the top of my head which model though.  I'll check for that when I get out of work as well.

**EDIT**  I found the keyboard and mouse I use by searching amazon.  Its the "Microsoft Wireless Optical Desktop Elite Executive Edition" (I know a mouth full).  Link is here :[http://www.amazon.com/Microsoft-Wireless-Optical-Elite-Executive/dp/B0009VPW80/ref=sr_1_16?ie=UTF8&s=electronics&qid=1252935574&sr=8-16]("http://www.amazon.com/Microsoft-Wireless-Optical-Elite-Executive/dp/B0009VPW80/ref=sr_1_16?ie=UTF8&s=electronics&qid=1252935574&sr=8-16")

---

### Post by P4man on 2009-09-14
is it possibly a bluetooth set? There are some open bugs with MS bluetooth mouse connection dropping. Before you go home from work, borrow a mouse for the evening :)

---

### Post by HolyShnikes on 2009-09-14
> **P4man said:**
> is it possibly a bluetooth set? There are some open bugs with MS bluetooth mouse connection dropping. Before you go home from work, borrow a mouse for the evening :)

Not Bluetooth.  When I bought it, bluetooth wasnt very popular yet.  In fact neither were laser mice.  I have another USB mouse at home, but I have  a feeling it will do the same thing if there is a problem with the USB Port.

---

### Post by HolyShnikes on 2009-09-14
I typed it in and this is what I got:

```
nathan@ubuntu:~$ sudo lsusb -v >usbinfo.txt
cannot read device status, Connection timed out (110)
nathan@ubuntu:~$ dmesg >log.txt
nathan@ubuntu:~$ 

```

Nothing comes up after dmesg.

Any ideas?

---

### Post by P4man on 2009-09-14
> **HolyShnikes said:**
> I typed it in and this is what I got:

```
nathan@ubuntu:~$ sudo lsusb -v >usbinfo.txt
cannot read device status, Connection timed out (110)
nathan@ubuntu:~$ dmesg >log.txt
nathan@ubuntu:~$ 

```

Nothing comes up after dmesg.

Any ideas?

eeh. those commands ought to make 2 files in your homefolder, called log.txt and usbinfo.txt. The idea was you could attach or paste relevant parts here.

If you want, you can also run them with**out** the ">filename" redirection, then you get the output onscreen.

That time out on the lsusb is already a bad sign though..

---

### Post by HolyShnikes on 2009-09-14
Got it.


```
Bus 002 Device 002: ID 067b:2506 Prolific Technology, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x067b Prolific Technology, Inc.
  idProduct          0x2506 
  bcdDevice            1.00
  iManufacturer           1 Prolific Technology Inc.
  iProduct                2 Mass Storage Device
  iSerial                 3 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
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
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
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

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.28-11-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:04.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0503 highspeed power enable connect
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.28-11-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:02.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 004 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x045e Microsoft Corp.
  idProduct          0x008c Wireless Intellimouse Explorer 2.0
  bcdDevice           73.73
  iManufacturer           1 Microsoft
  iProduct                2 Microsoft Wireless Optical Desktop® 1.00
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
    MaxPower              100mA
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
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     209
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0006  1x 6 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.28-11-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:04.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0303 lowspeed power enable connect
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x058f Alcor Micro Corp.
  idProduct          0x9360 8-in-1 Media Card Reader
  bcdDevice            1.00
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
      iInterface              0 
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
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.28-11-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:02.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0103 power enable connect
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled
```


Here is the log.txt


```
[    0.000000] BIOS EBDA/lowmem at: 0009d800/0009d800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: root=UUID=01C8E7A709C63B00 loop=/ubuntu/disks/root.disk ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afee0000 (usable)
[    0.000000]  BIOS-e820: 00000000afee0000 - 00000000afee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afee3000 - 00000000afef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afef0000 - 00000000aff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000b0000000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000240000000 (usable)
[    0.000000] DMI 2.5 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x240000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xafee0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009d800 (usable)
[    0.000000]  modified: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000afee0000 (usable)
[    0.000000]  modified: 00000000afee0000 - 00000000afee3000 (ACPI NVS)
[    0.000000]  modified: 00000000afee3000 - 00000000afef0000 (ACPI data)
[    0.000000]  modified: 00000000afef0000 - 00000000aff00000 (reserved)
[    0.000000]  modified: 00000000b0000000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000240000000 (usable)
[    0.000000] init_memory_mapping: 0000000000000000-00000000afee0000
[    0.000000]  0000000000 - 00afe00000 page 2M
[    0.000000]  00afe00000 - 00afee0000 page 4k
[    0.000000] kernel direct mapping tables up to afee0000 @ 10000-15000
[    0.000000] last_map_addr: afee0000 end: afee0000
[    0.000000] init_memory_mapping: 0000000100000000-0000000240000000
[    0.000000]  0100000000 - 0240000000 page 2M
[    0.000000] kernel direct mapping tables up to 240000000 @ 13000-1d000
[    0.000000] last_map_addr: 240000000 end: 240000000
[    0.000000] RAMDISK: 7f819000 - 7ffef6cb
[    0.000000] ACPI: RSDP 000F7500, 0024 (r2 Nvidia)
[    0.000000] ACPI: XSDT AFEE3100, 0044 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP AFEED300, 00F4 (r3 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] FADT: X_PM1a_EVT_BLK.bit_width (8) does not match PM1_EVT_LEN (4)
[    0.000000] ACPI Warning (tbfadt-0460): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20080926]
[    0.000000] ACPI: DSDT AFEE3280, A03A (r1 NVIDIA ASUSACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS AFEE0A80, 0040
[    0.000000] ACPI: HPET AFEED540, 0038 (r1 Nvidia ASUSACPI 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG AFEED5C0, 003C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC AFEED440, 008E (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0240000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [007f819000 - 007ffef6cb]          RAMDISK ==> [007f819000 - 007ffef6cb]
[    0.000000]   #4 [000009d800 - 0000100000]    BIOS reserved ==> [000009d800 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #6 [0000013000 - 0000018000]          PGTABLE ==> [0000013000 - 0000018000]
[    0.000000] found SMP MP-table at [ffff8800000f5970] 000f5970
[    0.000000]  [ffffe20000000000-ffffe20007dfffff] PMD -> [ffff880028200000-ffff88002fffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00240000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000afee0
[    0.000000]     0: 0x00100000 -> 0x00240000
[    0.000000] On node 0 totalpages: 2031213
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2548 pages reserved
[    0.000000]   DMA zone: 1377 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 702232 pages, LIFO batch:31
[    0.000000]   Normal zone: 17920 pages used for memmap
[    0.000000]   Normal zone: 1292800 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000afee0000 - 00000000afee3000
[    0.000000] PM: Registered nosave memory: 00000000afee3000 - 00000000afef0000
[    0.000000] PM: Registered nosave memory: 00000000afef0000 - 00000000aff00000
[    0.000000] PM: Registered nosave memory: 00000000aff00000 - 00000000b0000000
[    0.000000] PM: Registered nosave memory: 00000000b0000000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f4000000
[    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:30000000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1996409
[    0.000000] Kernel command line: root=UUID=01C8E7A709C63B00 loop=/ubuntu/disks/root.disk ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2598.866 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.004000] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] allocated 94371840 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 4884000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Your BIOS doesn't leave a aperture memory hole
[    0.004000] Please enable the IOMMU option in the BIOS setup
[    0.004000] This costs you 64 MB of RAM
[    0.004000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.004000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.004000] Memory: 7806560k/9437184k available (4760k kernel code, 1312332k absent, 317380k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5197.72 BogoMIPS (lpj=10395448)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] tseg: 00aff00000
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using C1E aware idle routine
[    0.004000] ACPI: Core revision 20080926
[    0.004918] ACPI: Checking initramfs for custom DSDT
[    0.236055] Setting APIC routing to flat
[    0.236564] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.276982] CPU0: AMD Phenom(tm) 9950 Quad-Core Processor stepping 03
[    0.280001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5200.17 BogoMIPS (lpj=10400356)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.364361] CPU1: AMD Phenom(tm) 9950 Quad-Core Processor stepping 03
[    0.364372] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.368071] Booting processor 2 APIC 0x2 ip 0x6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 5200.09 BogoMIPS (lpj=10400181)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.456358] CPU2: AMD Phenom(tm) 9950 Quad-Core Processor stepping 03
[    0.456368] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.460070] Booting processor 3 APIC 0x3 ip 0x6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 5200.05 BogoMIPS (lpj=10400110)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.548353] CPU3: AMD Phenom(tm) 9950 Quad-Core Processor stepping 03
[    0.548362] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.552030] Brought up 4 CPUs
[    0.552032] Total of 4 processors activated (20798.04 BogoMIPS).
[    0.552117] CPU0 attaching sched-domain:
[    0.552119]  domain 0: span 0-3 level CPU
[    0.552121]   groups: 0 1 2 3
[    0.552126] CPU1 attaching sched-domain:
[    0.552127]  domain 0: span 0-3 level CPU
[    0.552129]   groups: 1 2 3 0
[    0.552132] CPU2 attaching sched-domain:
[    0.552134]  domain 0: span 0-3 level CPU
[    0.552135]   groups: 2 3 0 1
[    0.552138] CPU3 attaching sched-domain:
[    0.552139]  domain 0: span 0-3 level CPU
[    0.552140]   groups: 3 0 1 2
[    0.552209] net_namespace: 1400 bytes
[    0.552209] Booting paravirtualized kernel on bare hardware
[    0.552246] Time: 15:38:54  Date: 09/14/09
[    0.552246] regulator: core version 0.5
[    0.552246] NET: Registered protocol family 16
[    0.552246] node 0 link 0: io port [7000, ffff]
[    0.552246] TOM: 00000000c0000000 aka 3072M
[    0.552246] Fam 10h mmconf [f0000000, f00fffff]
[    0.552246] node 0 link 0: mmio [a0000, bffff]
[    0.552246] node 0 link 0: mmio [c0000000, efffffff]
[    0.552246] node 0 link 0: mmio [f4000000, fe02ffff]
[    0.552246] node 0 link 0: mmio [f0000000, f06fffff] ==> [f0100000, f06fffff]
[    0.552246] TOM2: 0000000240000000 aka 9216M
[    0.552246] bus: [00,06] on node 0 link 0
[    0.552246] bus: 00 index 0 io port: [0, ffff]
[    0.552246] bus: 00 index 1 mmio: [a0000, bffff]
[    0.552246] bus: 00 index 2 mmio: [c0000000, efffffff]
[    0.552246] bus: 00 index 3 mmio: [f0700000, ffffffff]
[    0.552246] bus: 00 index 4 mmio: [f0100000, f06fffff]
[    0.552246] bus: 00 index 5 mmio: [240000000, fcffffffff]
[    0.552246] ACPI: bus type pci registered
[    0.552264] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.552266] PCI: MCFG area at f0000000 reserved in E820
[    0.554619] PCI: Using MMCONFIG at f0000000 - f3ffffff
[    0.554620] PCI: Using configuration type 1 for base access
[    0.557016] ACPI: EC: Look up EC in DSDT
[    0.572565] ACPI: Interpreter enabled
[    0.572569] ACPI: (supports S0 S1 S3 S4 S5)
[    0.572590] ACPI: Using IOAPIC for interrupt routing
[    0.593547] ACPI: No dock devices found.
[    0.593557] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.593796] pci 0000:00:01.1: reg 10 io port: [0xfc00-0xfc3f]
[    0.593805] pci 0000:00:01.1: reg 20 io port: [0x1c00-0x1c3f]
[    0.593809] pci 0000:00:01.1: reg 24 io port: [0x1c40-0x1c7f]
[    0.593819] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.593823] pci 0000:00:01.1: PME# disabled
[    0.593874] pci 0000:00:01.3: reg 10 32bit mmio: [0xfdf80000-0xfdffffff]
[    0.593987] pci 0000:00:02.0: reg 10 32bit mmio: [0xfe02f000-0xfe02ffff]
[    0.594004] pci 0000:00:02.0: supports D1 D2
[    0.594005] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.594008] pci 0000:00:02.0: PME# disabled
[    0.594028] pci 0000:00:02.1: reg 10 32bit mmio: [0xfe02e000-0xfe02e0ff]
[    0.594046] pci 0000:00:02.1: supports D1 D2
[    0.594047] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.594049] pci 0000:00:02.1: PME# disabled
[    0.594072] pci 0000:00:04.0: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.594089] pci 0000:00:04.0: supports D1 D2
[    0.594090] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.594092] pci 0000:00:04.0: PME# disabled
[    0.594112] pci 0000:00:04.1: reg 10 32bit mmio: [0xfe02c000-0xfe02c0ff]
[    0.594130] pci 0000:00:04.1: supports D1 D2
[    0.594131] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.594133] pci 0000:00:04.1: PME# disabled
[    0.594163] pci 0000:00:06.0: reg 20 io port: [0xf000-0xf00f]
[    0.594193] pci 0000:00:07.0: reg 10 32bit mmio: [0xfe020000-0xfe023fff]
[    0.594210] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.594212] pci 0000:00:07.0: PME# disabled
[    0.594254] pci 0000:00:09.0: reg 10 io port: [0x9f0-0x9f7]
[    0.594257] pci 0000:00:09.0: reg 14 io port: [0xbf0-0xbf3]
[    0.594259] pci 0000:00:09.0: reg 18 io port: [0x970-0x977]
[    0.594262] pci 0000:00:09.0: reg 1c io port: [0xb70-0xb73]
[    0.594265] pci 0000:00:09.0: reg 20 io port: [0xdc00-0xdc0f]
[    0.594267] pci 0000:00:09.0: reg 24 32bit mmio: [0xfe026000-0xfe027fff]
[    0.594294] pci 0000:00:0a.0: reg 10 32bit mmio: [0xfe02b000-0xfe02bfff]
[    0.594297] pci 0000:00:0a.0: reg 14 io port: [0xd800-0xd807]
[    0.594299] pci 0000:00:0a.0: reg 18 32bit mmio: [0xfe02a000-0xfe02a0ff]
[    0.594302] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xfe029000-0xfe02900f]
[    0.594312] pci 0000:00:0a.0: supports D1 D2
[    0.594313] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.594316] pci 0000:00:0a.0: PME# disabled
[    0.594337] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.594339] pci 0000:00:0b.0: PME# disabled
[    0.594479] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.594485] pci 0000:00:10.0: PME# disabled
[    0.594652] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.594658] pci 0000:00:12.0: PME# disabled
[    0.594824] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.594830] pci 0000:00:13.0: PME# disabled
[    0.594996] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.595002] pci 0000:00:14.0: PME# disabled
[    0.595123] pci 0000:01:0a.0: reg 10 32bit mmio: [0xfdeff000-0xfdefffff]
[    0.595148] pci 0000:01:0a.0: supports D1 D2
[    0.595149] pci 0000:01:0a.0: PME# supported from D0 D1 D2 D3hot
[    0.595152] pci 0000:01:0a.0: PME# disabled
[    0.595174] pci 0000:00:08.0: transparent bridge
[    0.595176] pci 0000:00:08.0: bridge io port: [0xc000-0xcfff]
[    0.595178] pci 0000:00:08.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.595181] pci 0000:00:08.0: bridge 32bit mmio pref: [0xfdd00000-0xfddfffff]
[    0.595195] pci 0000:02:00.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.595200] pci 0000:02:00.0: reg 14 64bit mmio: [0xd8000000-0xdfffffff]
[    0.595204] pci 0000:02:00.0: reg 1c 64bit mmio: [0xe6000000-0xe7ffffff]
[    0.595207] pci 0000:02:00.0: reg 24 io port: [0xbc00-0xbc7f]
[    0.595210] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.595227] pci 0000:00:0b.0: bridge io port: [0xb000-0xbfff]
[    0.595229] pci 0000:00:0b.0: bridge 32bit mmio: [0xfb000000-0xfcffffff]
[    0.595232] pci 0000:00:0b.0: bridge 64bit mmio pref: [0xd8000000-0xe7ffffff]
[    0.595281] pci 0000:00:10.0: bridge io port: [0xa000-0xafff]
[    0.595288] pci 0000:00:10.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.595300] pci 0000:00:10.0: bridge 64bit mmio pref: [0xfdb00000-0xfdbfffff]
[    0.595351] pci 0000:00:12.0: bridge io port: [0x9000-0x9fff]
[    0.595358] pci 0000:00:12.0: bridge 32bit mmio: [0xfda00000-0xfdafffff]
[    0.595371] pci 0000:00:12.0: bridge 64bit mmio pref: [0xfd900000-0xfd9fffff]
[    0.595421] pci 0000:00:13.0: bridge io port: [0x8000-0x8fff]
[    0.595428] pci 0000:00:13.0: bridge 32bit mmio: [0xfd800000-0xfd8fffff]
[    0.595441] pci 0000:00:13.0: bridge 64bit mmio pref: [0xfd700000-0xfd7fffff]
[    0.595492] pci 0000:00:14.0: bridge io port: [0x7000-0x7fff]
[    0.595499] pci 0000:00:14.0: bridge 32bit mmio: [0xfd600000-0xfd6fffff]
[    0.595511] pci 0000:00:14.0: bridge 64bit mmio pref: [0xfd500000-0xfd5fffff]
[    0.595561] bus 00 -> node 0
[    0.595567] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.596086] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.781480] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.781732] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.781986] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.782244] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 *11 14 15)
[    0.782498] ACPI: PCI Interrupt Link [LE0A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.782761] ACPI: PCI Interrupt Link [LE0B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.783023] ACPI: PCI Interrupt Link [LE0C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.783276] ACPI: PCI Interrupt Link [LE0D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.783529] ACPI: PCI Interrupt Link [LE1A] (IRQs 5 7 9 10 *11 14 15)
[    0.783782] ACPI: PCI Interrupt Link [LE1B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.784041] ACPI: PCI Interrupt Link [LE1C] (IRQs *5 7 9 10 11 14 15)
[    0.784295] ACPI: PCI Interrupt Link [LE1D] (IRQs 5 7 9 *10 11 14 15)
[    0.784542] ACPI: PCI Interrupt Link [LE2A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.784795] ACPI: PCI Interrupt Link [LE2B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.785049] ACPI: PCI Interrupt Link [LE2C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.785301] ACPI: PCI Interrupt Link [LE2D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.785554] ACPI: PCI Interrupt Link [LE3A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.785806] ACPI: PCI Interrupt Link [LE3B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.786059] ACPI: PCI Interrupt Link [LE3C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.786315] ACPI: PCI Interrupt Link [LE3D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.786568] ACPI: PCI Interrupt Link [LE4A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.786821] ACPI: PCI Interrupt Link [LE4B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.787076] ACPI: PCI Interrupt Link [LE4C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.787329] ACPI: PCI Interrupt Link [LE4D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.787582] ACPI: PCI Interrupt Link [LE5A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.787837] ACPI: PCI Interrupt Link [LE5B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.788096] ACPI: PCI Interrupt Link [LE5C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.788349] ACPI: PCI Interrupt Link [LE5D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.788604] ACPI: PCI Interrupt Link [LE6A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.788858] ACPI: PCI Interrupt Link [LE6B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.789112] ACPI: PCI Interrupt Link [LE6C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.789366] ACPI: PCI Interrupt Link [LE6D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.789619] ACPI: PCI Interrupt Link [LE7A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.789872] ACPI: PCI Interrupt Link [LE7B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.790125] ACPI: PCI Interrupt Link [LE7C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.790378] ACPI: PCI Interrupt Link [LE7D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.790631] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.790884] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
[    0.791138] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.791390] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 *7 9 10 11 14 15)
[    0.791643] ACPI: PCI Interrupt Link [LU1B] (IRQs *5 7 9 10 11 14 15)
[    0.791895] ACPI: PCI Interrupt Link [LU2B] (IRQs 5 7 9 *10 11 14 15)
[    0.792152] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
[    0.792404] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
[    0.792656] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 *7 9 10 11 14 15)
[    0.792913] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.793161] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.793424] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.793715] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.793994] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.794286] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.794570] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.794850] ACPI: PCI Interrupt Link [AE0A] (IRQs 16) *0, disabled.
[    0.795128] ACPI: PCI Interrupt Link [AE0B] (IRQs 16) *0, disabled.
[    0.795410] ACPI: PCI Interrupt Link [AE0C] (IRQs 16) *0, disabled.
[    0.795690] ACPI: PCI Interrupt Link [AE0D] (IRQs 16) *0, disabled.
[    0.795970] ACPI: PCI Interrupt Link [AE1A] (IRQs 16) *0
[    0.796250] ACPI: PCI Interrupt Link [AE1B] (IRQs 16) *0, disabled.
[    0.796531] ACPI: PCI Interrupt Link [AE1C] (IRQs 16) *0
[    0.796810] ACPI: PCI Interrupt Link [AE1D] (IRQs 16) *0
[    0.797089] ACPI: PCI Interrupt Link [AE2A] (IRQs 16) *0, disabled.
[    0.797370] ACPI: PCI Interrupt Link [AE2B] (IRQs 16) *0, disabled.
[    0.797651] ACPI: PCI Interrupt Link [AE2C] (IRQs 16) *0, disabled.
[    0.797932] ACPI: PCI Interrupt Link [AE2D] (IRQs 16) *0, disabled.
[    0.798211] ACPI: PCI Interrupt Link [AE3A] (IRQs 16) *0, disabled.
[    0.798491] ACPI: PCI Interrupt Link [AE3B] (IRQs 16) *0, disabled.
[    0.798772] ACPI: PCI Interrupt Link [AE3C] (IRQs 16) *0, disabled.
[    0.799063] ACPI: PCI Interrupt Link [AE3D] (IRQs 16) *0, disabled.
[    0.799339] ACPI: PCI Interrupt Link [AE4A] (IRQs 16) *0, disabled.
[    0.799620] ACPI: PCI Interrupt Link [AE4B] (IRQs 16) *0, disabled.
[    0.799905] ACPI: PCI Interrupt Link [AE4C] (IRQs 16) *0, disabled.
[    0.800190] ACPI: PCI Interrupt Link [AE4D] (IRQs 16) *0, disabled.
[    0.800466] ACPI: PCI Interrupt Link [AE5A] (IRQs 16) *0, disabled.
[    0.800746] ACPI: PCI Interrupt Link [AE5B] (IRQs 16) *0, disabled.
[    0.801027] ACPI: PCI Interrupt Link [AE5C] (IRQs 16) *0, disabled.
[    0.801309] ACPI: PCI Interrupt Link [AE5D] (IRQs 16) *0, disabled.
[    0.801590] ACPI: PCI Interrupt Link [AE6A] (IRQs 16) *0, disabled.
[    0.801869] ACPI: PCI Interrupt Link [AE6B] (IRQs 16) *0, disabled.
[    0.802155] ACPI: PCI Interrupt Link [AE6C] (IRQs 16) *0, disabled.
[    0.802433] ACPI: PCI Interrupt Link [AE6D] (IRQs 16) *0, disabled.
[    0.802714] ACPI: PCI Interrupt Link [AE7A] (IRQs 16) *0, disabled.
[    0.802994] ACPI: PCI Interrupt Link [AE7B] (IRQs 16) *0, disabled.
[    0.803275] ACPI: PCI Interrupt Link [AE7C] (IRQs 16) *0, disabled.
[    0.803555] ACPI: PCI Interrupt Link [AE7D] (IRQs 16) *0, disabled.
[    0.803839] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[    0.804121] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[    0.804402] ACPI: PCI Interrupt Link [AUB2] (IRQs 20 21 22 23) *0
[    0.804677] ACPI: PCI Interrupt Link [AU1B] (IRQs 20 21 22 23) *0
[    0.804956] ACPI: PCI Interrupt Link [AU2B] (IRQs 20 21 22 23) *0
[    0.805236] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.805516] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[    0.805796] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.806077] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.806357] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.806639] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.806919] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.807114] ACPI: WMI: Mapper loaded
[    0.807168] SCSI subsystem initialized
[    0.807168] libata version 3.00 loaded.
[    0.807168] usbcore: registered new interface driver usbfs
[    0.807168] usbcore: registered new interface driver hub
[    0.807168] usbcore: registered new device driver usb
[    0.807168] PCI: Using ACPI for IRQ routing
[    0.820008] Bluetooth: Core ver 2.13
[    0.820019] NET: Registered protocol family 31
[    0.820019] Bluetooth: HCI device and connection manager initialized
[    0.820019] Bluetooth: HCI socket layer initialized
[    0.820019] NET: Registered protocol family 8
[    0.820019] NET: Registered protocol family 20
[    0.820026] NetLabel: Initializing
[    0.820027] NetLabel:  domain hash size = 128
[    0.820028] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.820039] NetLabel:  unlabeled traffic allowed by default
[    0.820293] PCI-DMA: Disabling AGP.
[    0.820349] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.820350] PCI-DMA: using GART IOMMU.
[    0.820353] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.821759] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.821764] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.832066] AppArmor: AppArmor Filesystem Enabled
[    0.836010] Switched to high resolution mode on CPU 0
[    0.836397] Switched to high resolution mode on CPU 3
[    0.836401] Switched to high resolution mode on CPU 1
[    0.836405] Switched to high resolution mode on CPU 2
[    0.848021] pnp: PnP ACPI init
[    0.848036] ACPI: bus type pnp registered
[    0.857893] pnp: PnP ACPI: found 13 devices
[    0.857895] ACPI: ACPI bus type pnp unregistered
[    0.857904] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.857906] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.857908] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.857910] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.857912] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.857914] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.857916] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[    0.857919] system 00:01: iomem range 0xb0000000-0xbfffffff has been reserved
[    0.857923] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.857925] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.857926] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.857931] system 00:0b: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.857935] system 00:0c: iomem range 0xcd000-0xcffff has been reserved
[    0.857937] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.857939] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.857941] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.857943] system 00:0c: iomem range 0xfeff0000-0xfeff00ff has been reserved
[    0.857945] system 00:0c: iomem range 0xafee0000-0xafefffff could not be reserved
[    0.857947] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[    0.857949] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.857951] system 00:0c: iomem range 0x100000-0xafedffff could not be reserved
[    0.857953] system 00:0c: iomem range 0xafff0000-0xbffeffff could not be reserved
[    0.857955] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.857957] system 00:0c: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.857959] system 00:0c: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.857961] system 00:0c: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.857963] system 00:0c: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.857965] system 00:0c: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.862628] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.862631] pci 0000:00:08.0:   IO window: 0xc000-0xcfff
[    0.862634] pci 0000:00:08.0:   MEM window: 0xfde00000-0xfdefffff
[    0.862637] pci 0000:00:08.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.862642] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.862644] pci 0000:00:0b.0:   IO window: 0xb000-0xbfff
[    0.862646] pci 0000:00:0b.0:   MEM window: 0xfb000000-0xfcffffff
[    0.862649] pci 0000:00:0b.0:   PREFETCH window: 0x000000d8000000-0x000000e7ffffff
[    0.862651] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.862656] pci 0000:00:10.0:   IO window: 0xa000-0xafff
[    0.862665] pci 0000:00:10.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.862671] pci 0000:00:10.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
[    0.862683] pci 0000:00:12.0: PCI bridge, secondary bus 0000:04
[    0.862687] pci 0000:00:12.0:   IO window: 0x9000-0x9fff
[    0.862696] pci 0000:00:12.0:   MEM window: 0xfda00000-0xfdafffff
[    0.862702] pci 0000:00:12.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.862714] pci 0000:00:13.0: PCI bridge, secondary bus 0000:05
[    0.862718] pci 0000:00:13.0:   IO window: 0x8000-0x8fff
[    0.862727] pci 0000:00:13.0:   MEM window: 0xfd800000-0xfd8fffff
[    0.862734] pci 0000:00:13.0:   PREFETCH window: 0x000000fd700000-0x000000fd7fffff
[    0.862746] pci 0000:00:14.0: PCI bridge, secondary bus 0000:06
[    0.862750] pci 0000:00:14.0:   IO window: 0x7000-0x7fff
[    0.862759] pci 0000:00:14.0:   MEM window: 0xfd600000-0xfd6fffff
[    0.862765] pci 0000:00:14.0:   PREFETCH window: 0x000000fd500000-0x000000fd5fffff
[    0.862781] pci 0000:00:08.0: setting latency timer to 64
[    0.862785] pci 0000:00:0b.0: setting latency timer to 64
[    0.863207] ACPI: PCI Interrupt Link [AE0A] enabled at IRQ 16
[    0.863215] pci 0000:00:10.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[    0.863223] pci 0000:00:10.0: setting latency timer to 64
[    0.863631] ACPI: PCI Interrupt Link [AE2A] enabled at IRQ 16
[    0.863638] pci 0000:00:12.0: PCI INT A -> Link[AE2A] -> GSI 16 (level, low) -> IRQ 16
[    0.863645] pci 0000:00:12.0: setting latency timer to 64
[    0.864079] ACPI: PCI Interrupt Link [AE3A] enabled at IRQ 16
[    0.864081] pci 0000:00:13.0: PCI INT A -> Link[AE3A] -> GSI 16 (level, low) -> IRQ 16
[    0.864088] pci 0000:00:13.0: setting latency timer to 64
[    0.864483] ACPI: PCI Interrupt Link [AE4A] enabled at IRQ 16
[    0.864490] pci 0000:00:14.0: PCI INT A -> Link[AE4A] -> GSI 16 (level, low) -> IRQ 16
[    0.864497] pci 0000:00:14.0: setting latency timer to 64
[    0.864502] bus: 00 index 0 io port: [0x00-0xffff]
[    0.864503] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.864505] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.864507] bus: 01 index 1 mmio: [0xfde00000-0xfdefffff]
[    0.864509] bus: 01 index 2 mmio: [0xfdd00000-0xfddfffff]
[    0.864510] bus: 01 index 3 io port: [0x00-0xffff]
[    0.864512] bus: 01 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.864513] bus: 02 index 0 io port: [0xb000-0xbfff]
[    0.864515] bus: 02 index 1 mmio: [0xfb000000-0xfcffffff]
[    0.864516] bus: 02 index 2 mmio: [0xd8000000-0xe7ffffff]
[    0.864518] bus: 02 index 3 mmio: [0x0-0x0]
[    0.864519] bus: 03 index 0 io port: [0xa000-0xafff]
[    0.864520] bus: 03 index 1 mmio: [0xfdc00000-0xfdcfffff]
[    0.864522] bus: 03 index 2 mmio: [0xfdb00000-0xfdbfffff]
[    0.864523] bus: 03 index 3 mmio: [0x0-0x0]
[    0.864524] bus: 04 index 0 io port: [0x9000-0x9fff]
[    0.864526] bus: 04 index 1 mmio: [0xfda00000-0xfdafffff]
[    0.864527] bus: 04 index 2 mmio: [0xfd900000-0xfd9fffff]
[    0.864528] bus: 04 index 3 mmio: [0x0-0x0]
[    0.864530] bus: 05 index 0 io port: [0x8000-0x8fff]
[    0.864531] bus: 05 index 1 mmio: [0xfd800000-0xfd8fffff]
[    0.864533] bus: 05 index 2 mmio: [0xfd700000-0xfd7fffff]
[    0.864534] bus: 05 index 3 mmio: [0x0-0x0]
[    0.864535] bus: 06 index 0 io port: [0x7000-0x7fff]
[    0.864536] bus: 06 index 1 mmio: [0xfd600000-0xfd6fffff]
[    0.864538] bus: 06 index 2 mmio: [0xfd500000-0xfd5fffff]
[    0.864539] bus: 06 index 3 mmio: [0x0-0x0]
[    0.864548] NET: Registered protocol family 2
[    0.900063] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.900643] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.901817] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.902120] TCP: Hash tables configured (established 262144 bind 65536)
[    0.902122] TCP reno registered
[    0.912080] NET: Registered protocol family 1
[    0.912175] checking if image is initramfs... it is
[    1.367136] Freeing initrd memory: 8025k freed
[    1.370043] audit: initializing netlink socket (disabled)
[    1.370060] type=2000 audit(1252942734.368:1): initialized
[    1.376082] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.377123] VFS: Disk quotas dquot_6.5.1
[    1.377165] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.377612] fuse init (API version 7.10)
[    1.377670] msgmni has been set to 15264
[    1.377812] alg: No test for stdrng (krng)
[    1.377824] io scheduler noop registered
[    1.377826] io scheduler anticipatory registered
[    1.377827] io scheduler deadline registered
[    1.377857] io scheduler cfq registered (default)
[    1.417603] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.417631] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.417659] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.417687] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.417714] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.417769] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.417834] pci 0000:00:12.0: Enabling HT MSI Mapping
[    1.417899] pci 0000:00:13.0: Enabling HT MSI Mapping
[    1.417964] pci 0000:00:14.0: Enabling HT MSI Mapping
[    1.418007] pci 0000:02:00.0: Boot video device
[    1.434413] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    1.434581] pcieport-driver 0000:00:10.0: found MSI capability
[    1.434662] pcieport-driver 0000:00:10.0: irq 2303 for MSI/MSI-X
[    1.434695] pci_express 0000:00:10.0:pcie00: allocate port service
[    1.434868] pcieport-driver 0000:00:12.0: setting latency timer to 64
[    1.435035] pcieport-driver 0000:00:12.0: found MSI capability
[    1.435119] pcieport-driver 0000:00:12.0: irq 2302 for MSI/MSI-X
[    1.435151] pci_express 0000:00:12.0:pcie00: allocate port service
[    1.435323] pcieport-driver 0000:00:13.0: setting latency timer to 64
[    1.435489] pcieport-driver 0000:00:13.0: found MSI capability
[    1.435574] pcieport-driver 0000:00:13.0: irq 2301 for MSI/MSI-X
[    1.435606] pci_express 0000:00:13.0:pcie00: allocate port service
[    1.435776] pcieport-driver 0000:00:14.0: setting latency timer to 64
[    1.435943] pcieport-driver 0000:00:14.0: found MSI capability
[    1.436027] pcieport-driver 0000:00:14.0: irq 2300 for MSI/MSI-X
[    1.436059] pci_express 0000:00:14.0:pcie00: allocate port service
[    1.436199] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.436205] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.436334] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.436336] ACPI: Power Button (FF) [PWRF]
[    1.436365] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.436366] ACPI: Power Button (CM) [PWRB]
[    1.436428] fan PNP0C0B:00: registered as cooling_device0
[    1.436432] ACPI: Fan [FAN] (on)
[    1.436901] processor ACPI_CPU:00: registered as cooling_device1
[    1.436925] processor ACPI_CPU:01: registered as cooling_device2
[    1.436948] processor ACPI_CPU:02: registered as cooling_device3
[    1.436969] processor ACPI_CPU:03: registered as cooling_device4
[    1.446648] ACPI Warning (nspredef-0858): \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference [20080926]
[    1.446654] ACPI: Expecting a [Reference] package element, found type 0
[    1.446949] thermal LNXTHERM:01: registered as thermal_zone0
[    1.447484] ACPI: Thermal Zone [THRM] (40 C)
[    1.473740] Linux agpgart interface v0.103
[    1.473748] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.473835] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.474050] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.474508] brd: module loaded
[    1.474693] loop: module loaded
[    1.474741] Fixed MDIO Bus: probed
[    1.474745] PPP generic driver version 2.4.2
[    1.474783] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.474810] Driver 'sd' needs updating - please use bus_type methods
[    1.474816] Driver 'sr' needs updating - please use bus_type methods
[    1.474845] ahci 0000:00:09.0: version 3.0
[    1.475305] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    1.475315] ahci 0000:00:09.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.475353] ahci 0000:00:09.0: irq 2299 for MSI/MSI-X
[    1.475403] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.475406] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    1.475408] ahci 0000:00:09.0: setting latency timer to 64
[    1.475740] scsi0 : ahci
[    1.475816] scsi1 : ahci
[    1.475860] scsi2 : ahci
[    1.475901] scsi3 : ahci
[    1.475938] scsi4 : ahci
[    1.475976] scsi5 : ahci
[    1.476066] ata1: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026100 irq 2299
[    1.476068] ata2: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026180 irq 2299
[    1.476071] ata3: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026200 irq 2299
[    1.476073] ata4: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026280 irq 2299
[    1.476075] ata5: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026300 irq 2299
[    1.476077] ata6: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026380 irq 2299
[    1.960076] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.969155] ata1.00: ATA-8: WDC WD5000AAJS-22A8B0, 01.03B01, max UDMA/133
[    1.969157] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.970110] ata1.00: configured for UDMA/133
[    2.288022] ata2: SATA link down (SStatus 0 SControl 300)
[    3.176063] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.186884] ata3.00: ATA-8: WDC WD5000AAJS-22YFA0, 12.01C02, max UDMA/133
[    3.186886] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.187651] ata3.00: configured for UDMA/133
[    3.504025] ata4: SATA link down (SStatus 0 SControl 300)
[    3.824012] ata5: SATA link down (SStatus 0 SControl 300)
[    4.144012] ata6: SATA link down (SStatus 0 SControl 300)
[    4.144096] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAJS-2 01.0 PQ: 0 ANSI: 5
[    4.144156] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    4.144167] sd 0:0:0:0: [sda] Write Protect is off
[    4.144169] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.144183] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.144230] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    4.144239] sd 0:0:0:0: [sda] Write Protect is off
[    4.144241] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.144256] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.144261]  sda: sda1 sda2
[    4.149284] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.149314] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.149351] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAJS-2 12.0 PQ: 0 ANSI: 5
[    4.149399] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    4.149407] sd 2:0:0:0: [sdb] Write Protect is off
[    4.149409] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.149425] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.149457] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    4.149465] sd 2:0:0:0: [sdb] Write Protect is off
[    4.149467] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.149485] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.149490]  sdb: sdb1
[    4.154589] sd 2:0:0:0: [sdb] Attached SCSI disk
[    4.154611] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    4.154764] pata_amd 0000:00:06.0: version 0.3.10
[    4.154794] pata_amd 0000:00:06.0: setting latency timer to 64
[    4.154877] scsi6 : pata_amd
[    4.154917] scsi7 : pata_amd
[    4.155655] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    4.155657] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    4.324359] ata7.00: ATAPI: HL-DT-STDVD-ROM GDR8161B, 0045, max UDMA/33
[    4.324379] ata7.01: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB04, max UDMA/33
[    4.324404] ata7: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x1f)
[    4.324408] ata7: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x1f)
[    4.340251] ata7.00: configured for UDMA/33
[    4.356231] ata7.01: configured for UDMA/33
[    4.357012] ata8: port disabled. ignoring.
[    4.363469] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8161B 0045 PQ: 0 ANSI: 5
[    4.376678] sr0: scsi3-mmc drive: 20x/48x cd/rw xa/form2 cdda tray
[    4.376680] Uniform CD-ROM driver Revision: 3.20
[    4.376752] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    4.376777] sr 6:0:0:0: Attached scsi generic sg2 type 5
[    4.377558] scsi 6:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-S182M SB04 PQ: 0 ANSI: 5
[    4.384123] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.384160] sr 6:0:1:0: Attached scsi CD-ROM sr1
[    4.384180] sr 6:0:1:0: Attached scsi generic sg3 type 5
[    4.384455] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.384922] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 22
[    4.384931] ehci_hcd 0000:00:02.1: PCI INT B -> Link[AUB2] -> GSI 22 (level, low) -> IRQ 22
[    4.384946] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    4.384948] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    4.384989] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    4.385011] ehci_hcd 0000:00:02.1: debug port 1
[    4.385015] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    4.385032] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    4.396031] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    4.396080] usb usb1: configuration #1 chosen from 1 choice
[    4.396099] hub 1-0:1.0: USB hub found
[    4.396105] hub 1-0:1.0: 6 ports detected
[    4.396438] ACPI: PCI Interrupt Link [AU2B] disabled and referenced, BIOS bug
[    4.396612] ACPI: PCI Interrupt Link [AU2B] enabled at IRQ 21
[    4.396619] ehci_hcd 0000:00:04.1: PCI INT B -> Link[AU2B] -> GSI 21 (level, low) -> IRQ 21
[    4.396626] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    4.396628] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    4.396655] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    4.396674] ehci_hcd 0000:00:04.1: debug port 1
[    4.396677] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    4.396692] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfe02c000
[    4.408019] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    4.408060] usb usb2: configuration #1 chosen from 1 choice
[    4.408074] hub 2-0:1.0: USB hub found
[    4.408079] hub 2-0:1.0: 6 ports detected
[    4.408146] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.408587] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 20
[    4.408593] ohci_hcd 0000:00:02.0: PCI INT A -> Link[AUBA] -> GSI 20 (level, low) -> IRQ 20
[    4.408601] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    4.408603] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    4.408631] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    4.408651] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfe02f000
[    4.466064] usb usb3: configuration #1 chosen from 1 choice
[    4.466080] hub 3-0:1.0: USB hub found
[    4.466086] hub 3-0:1.0: 6 ports detected
[    4.466567] ACPI: PCI Interrupt Link [AU1B] enabled at IRQ 23
[    4.466570] ohci_hcd 0000:00:04.0: PCI INT A -> Link[AU1B] -> GSI 23 (level, low) -> IRQ 23
[    4.466577] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    4.466579] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    4.466604] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    4.466621] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfe02d000
[    4.522042] usb usb4: configuration #1 chosen from 1 choice
[    4.522059] hub 4-0:1.0: USB hub found
[    4.522064] hub 4-0:1.0: 6 ports detected
[    4.522125] uhci_hcd: USB Universal Host Controller Interface driver
[    4.522163] usbcore: registered new interface driver libusual
[    4.522185] usbcore: registered new interface driver usbserial
[    4.522192] USB Serial support registered for generic
[    4.522201] usbcore: registered new interface driver usbserial_generic
[    4.522202] usbserial: USB Serial Driver core
[    4.522234] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    4.522236] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    4.522306] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.533536] mice: PS/2 mouse device common for all mice
[    4.569571] rtc_cmos 00:05: RTC can wake from S4
[    4.569596] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    4.569650] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    4.569689] device-mapper: uevent: version 1.0.3
[    4.569763] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.569857] device-mapper: multipath: version 1.0.5 loaded
[    4.569859] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.569963] cpuidle: using governor ladder
[    4.569965] cpuidle: using governor menu
[    4.570287] TCP cubic registered
[    4.570332] NET: Registered protocol family 10
[    4.570619] lo: Disabled Privacy Extensions
[    4.570829] NET: Registered protocol family 17
[    4.570844] Bluetooth: L2CAP ver 2.11
[    4.570845] Bluetooth: L2CAP socket layer initialized
[    4.570847] Bluetooth: SCO (Voice Link) ver 0.6
[    4.570848] Bluetooth: SCO socket layer initialized
[    4.570875] Bluetooth: RFCOMM socket layer initialized
[    4.570880] Bluetooth: RFCOMM TTY layer initialized
[    4.570881] Bluetooth: RFCOMM ver 1.10
[    4.570931] powernow-k8: Found 1 AMD Phenom(tm) 9950 Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
[    4.570946] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    4.571037] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    4.571123] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    4.571212] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    4.571363] registered taskstats version 1
[    4.571478]   Magic number: 9:242:639
[    4.571590] rtc_cmos 00:05: setting system clock to 2009-09-14 15:38:58 UTC (1252942738)
[    4.571592] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.571594] EDD information not available.
[    4.571622] Freeing unused kernel memory: 536k freed
[    4.571787] Write protecting the kernel read-only data: 6708k
[    4.587505] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.730740] Floppy drive(s): fd0 is 1.44M
[    4.755769] FDC 0 is a post-1991 82077
[    4.758487] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    4.758498] ohci1394 0000:01:0a.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    4.775080] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.775537] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    4.775540] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[    4.775544] forcedeth 0000:00:0a.0: setting latency timer to 64
[    4.810252] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    4.838294] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:15:1b:10:48
[    4.838298] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
[    4.876543] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    5.007366] usb 2-2: configuration #1 chosen from 1 choice
[    5.010194] Initializing USB Mass Storage driver...
[    5.011035] scsi8 : SCSI emulation for USB Mass Storage devices
[    5.011120] usbcore: registered new interface driver usb-storage
[    5.011123] USB Mass Storage support registered.
[    5.011214] usb-storage: device found at 2
[    5.011215] usb-storage: waiting for device to settle before scanning
[    5.364031] usb 4-3: new low speed USB device using ohci_hcd and address 2
[    5.401988] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.401991] EXT3-fs: write access will be enabled during recovery.
[    5.582571] usb 4-3: configuration #1 chosen from 1 choice
[    5.589127] usbcore: registered new interface driver hiddev
[    5.600855] input: Microsoft Microsoft Wireless Optical Desktop® 1.00 as /devices/pci0000:00/0000:00:04.0/usb4/4-3/4-3:1.0/input/input4
[    5.629605] generic-usb 0003:045E:008C.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 1.00] on usb-0000:00:04.0-3/input0
[    5.629623] usbcore: registered new interface driver usbhid
[    5.629625] usbhid: v2.6:USB HID core driver
[    5.888673] usb 3-5: new full speed USB device using ohci_hcd and address 2
[    5.990425] kjournald starting.  Commit interval 5 seconds
[    5.990434] EXT3-fs: recovery complete.
[    5.990545] EXT3-fs: mounted filesystem with ordered data mode.
[    6.092143] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c00014f44d1]
[    6.103837] usb 3-5: configuration #1 chosen from 1 choice
[    6.106875] scsi9 : SCSI emulation for USB Mass Storage devices
[    6.107014] usb-storage: device found at 2
[    6.107016] usb-storage: waiting for device to settle before scanning
[    9.145309] udev: starting version 141
[    9.341296] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.388380] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    9.572049] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[    9.572054] HDA Intel 0000:00:07.0: PCI INT A -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[    9.572112] HDA Intel 0000:00:07.0: setting latency timer to 64
[   10.008210] usb-storage: device scan complete
[   10.043575] scsi 8:0:0:0: Direct-Access     ST312002 6A               8.01 PQ: 0 ANSI: 0
[   10.044811] sd 8:0:0:0: [sdc] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[   10.048328] sd 8:0:0:0: [sdc] Write Protect is off
[   10.048331] sd 8:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   10.048333] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[   10.049188] sd 8:0:0:0: [sdc] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[   10.051313] sd 8:0:0:0: [sdc] Write Protect is off
[   10.051315] sd 8:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   10.051316] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[   10.051319]  sdc: sdc1
[   10.057881] sd 8:0:0:0: [sdc] Attached SCSI disk
[   10.057957] sd 8:0:0:0: Attached scsi generic sg4 type 0
[   10.497129] lp: driver loaded but no devices found
[   11.077705] EXT3 FS on loop0, internal journal
[   11.106992] usb-storage: device scan complete
[   11.113992] scsi 9:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   11.120988] scsi 9:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   11.127978] scsi 9:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   11.134994] scsi 9:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   11.183096] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[   11.183146] sd 9:0:0:0: Attached scsi generic sg5 type 0
[   11.231120] sd 9:0:0:1: [sde] Attached SCSI removable disk
[   11.231171] sd 9:0:0:1: Attached scsi generic sg6 type 0
[   11.300138] sd 9:0:0:2: [sdf] Attached SCSI removable disk
[   11.300187] sd 9:0:0:2: Attached scsi generic sg7 type 0
[   11.380189] sd 9:0:0:3: [sdg] Attached SCSI removable disk
[   11.380241] sd 9:0:0:3: Attached scsi generic sg8 type 0
[   13.270881] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k
[   13.352032] type=1505 audit(1252957147.277:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2472
[   13.384589] type=1505 audit(1252957147.309:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2476
[   13.384679] type=1505 audit(1252957147.309:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2476
[   13.384709] type=1505 audit(1252957147.309:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2476
[   13.384734] type=1505 audit(1252957147.309:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2476
[   13.475204] type=1505 audit(1252957147.401:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2481
[   13.475327] type=1505 audit(1252957147.401:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2481
[   13.496860] type=1505 audit(1252957147.421:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2485
[   14.765277] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.765280] Bluetooth: BNEP filters: protocol multicast
[   14.783602] Bridge firewalling registered
[   15.632445] ppdev: user-space parallel port driver
[   20.073270] forcedeth 0000:00:0a.0: irq 2298 for MSI/MSI-X
[   20.528380] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[   20.528383] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[   30.628507] eth0: no IPv6 routers present
[   37.405982] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[   37.405985] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[   51.699078] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[   51.699081] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[   53.388169] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[   53.388172] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[   68.362271] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[   69.361965] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[   70.361903] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[   75.361590] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 0 len 2 ret -110
[   85.794365] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[   86.794298] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[   87.794243] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[   92.793925] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 0 len 2 ret -110
[  136.790930] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  136.790933] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  137.412883] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  137.412886] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  148.767765] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  148.767768] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  151.987069] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  151.987072] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  155.419752] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  155.419755] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  158.228561] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  158.228564] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  162.809373] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  162.809376] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  171.185443] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  171.185446] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  178.813613] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  178.813616] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  196.285071] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  196.285074] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  196.785825] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  196.785827] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  206.174836] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  206.174839] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  209.243281] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  209.243284] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  211.850691] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  211.850694] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  229.462915] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  229.462918] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  278.647338] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  278.647341] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  283.308977] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  283.308980] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  297.751962] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  297.751965] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  304.165636] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[  305.166074] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[  306.166511] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[  311.165699] usb 3-5: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 0 len 2 ret -110
```

---

### Post by P4man on 2009-09-14
Hmmm.. can't point to anything obviously wrong.  Can't find a similar problem with that mouse either.

perhaps it would be interesting you could rerun those commands when your mouse froze. To do so keyboard only, open a tty with control+alt+F1 or press alt+F2 to start gnome-terminal.

After making those files, see what happens when you remove and reinsert the usb receiver.

---

### Post by HolyShnikes on 2009-09-14
Okay, so I did some searching around, and it turns out that the problem is the hardware on my USB.  I figured it out because it was doing it in windows vista a little while ago.  It just so happened to be doing it while I installed ubuntu.  I took the computer apart and found a loose connection that was near one of the cooling fans.  The fan would spin and knock it in and out of alignment.

So weird 0_o

Thanks so much for the help though.

---

