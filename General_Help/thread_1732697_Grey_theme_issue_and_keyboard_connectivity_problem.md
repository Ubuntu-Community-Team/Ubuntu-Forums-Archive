---
title: "Grey theme issue and keyboard connectivity problems"
date: 2011-04-18
forum: General Help
---

### Post by 1984dc on 2011-04-18
Hello every1  ):P

I have just installed Ubuntu 10.10 powerpc on my powermac G5  and i am noticing some erratic behavior.

I pressed ctrl + mute to see if there was a keyboard shortcut assigned to those keys and suddenly all the icons and theme changed to a nasty grey style. I can get the basic theme to go back minus the panels applications and icons. I had this problem on my laptop too and never found a solution (please see pic below of ppc) 

[IMG]http://img98.imageshack.us/img98/1719/greytheme.png[/IMG]

Also subsequently (and i don't think its connected necessarily) my keyboard has been not responding sporadically. I unplug it and wait for a min and then plug it back in and it seems to work again??

Below are a few error messages that i found from the logs that i hope someone might be able to help me understand the problem;
[U]
[COLOR=Red]Grey theme possible error messages from the log viewer[/COLOR]
[COLOR=Navy]
Apr 14 20:42:44 G5-ubuntu-10 pbbuttonsd: ERROR: The object '/dev/adb' doesn't exist.
Apr 14 20:42:44 G5-ubuntu-10 pbbuttonsd: WARNING: No backlight driver available - check your Kernel configuration.
Apr 14 20:42:44 G5-ubuntu-10 pbbuttonsd: ERROR: The object '/dev/adb' doesn't exist.
Apr 14 20:42:44 G5-ubuntu-10 kernel: [   12.294434] ioctl32(pbbuttonsd:1072): Unknown cmd fd(10) cmd(40044201){t:'B';sz:4} arg(ff81160c) on /dev/pmu
Apr 14 20:42:44 G5-ubuntu-10 kernel: [   12.313926] [drm] radeon defaulting to kernel modesetting.
Apr 14 20:42:44 G5-ubuntu-10 kernel: [   12.313932] [drm] radeon kernel modesetting enabled.
Apr 14 20:42:44 G5-ubuntu-10 kernel: [   12.475813] RPC: Registered udp transport module.
Apr 14 20:42:44 G5-ubuntu-10 kernel: [   12.475818] RPC: Registered tcp transport module.
Apr 14 20:42:44 G5-ubuntu-10 kernel: [   12.475821] RPC: Registered tcp NFSv4.1 backchannel transport module.
Apr 14 20:42:44 G5-ubuntu-10 kernel: [   12.520293] Installing knfsd (copyright (C) 1996 [EMAIL="okir@monad.swb.de"]okir@monad.swb.de[/EMAIL]).
Apr 14 20:42:44 G5-ubuntu-10 kernel: [   12.569726] svc: failed to register lockdv1 RPC service (errno 97).
Apr 14 20:42:44 G5-ubuntu-10 kernel: [   12.579787] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Apr 14 20:42:44 G5-ubuntu-10 kernel: [   12.580120] NFSD: starting 90-second grace period
Apr 14 20:42:44 G5-ubuntu-10 dhclient: isc-dhclient-V3.1.3
Apr 14 20:42:44 G5-ubuntu-10 dhclient: isc-dhclient-V3.1.3
Apr 14 20:42:46 G5-ubuntu-10 gdm-session-worker[1268]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory

Apr 14 20:42:44 G5-ubuntu-10 kernel: [   12.569726] svc: failed to register lockdv1 RPC service (errno 97).

Apr 14 20:42:47 G5-ubuntu-10 gdm-simple-greeter[1265]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow

Apr 14 20:44:17 G5-ubuntu-10 gdm-simple-greeter[1265]: WARNING: SelectLayout org.freedesktop.DBus.Error.NoReply raised: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.#012

Apr 14 20:44:17 G5-ubuntu-10 gdm-simple-slave[990]: WARNING: GreeterServer: Not connected!

Apr 14 20:48:03 G5-ubuntu-10 gdm-simple-greeter[2201]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Apr 14 20:48:04 G5-ubuntu-10 gdm-session-worker[2204]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 14 20:48:09 G5-ubuntu-10 kernel: [  337.431731] /build/buildd/linux-2.6.35/drivers/hid/usbhid/hid-core.c: can't reset device, 0001:02:0b.2-4.2.2/input1, status -71

[/COLOR]
[COLOR=Red]
Keyboard cutting-out possible error message from the log viewer[/COLOR]

[COLOR=Navy]Apr 14 20:43:36 G5-ubuntu-10 kernel: [   64.640246] usb 4-1: USB disconnect, address 2[/COLOR]

[/U]
Any help on either of these issues would be hugely appreciated.

Many thanks in advance.

Dc

Powermac G5
ubuntu 10.10

---

### Post by 1984dc on 2011-04-19
After speaking to Wizard (many thanks btw) on the #ubuntu-powerpc irc channel, I think i may have got to the problem with the grey screen. Wizard recommended that i check to see if the gnome-settings-deamon was working. So ater i restarted it i got my original theme back (result!), but....(there always has to be a "but" doesn't there!). now my keyboard doesn't work at all.
 
any suggestions people?
 
Ps Wizard if you read this; sorry for my swift departure last night i was battling to get my keyboard working and ran out of time to log back in to the irc using my apple partition. Thank's for all your help ;)

---

### Post by 1984dc on 2011-04-19
This is the readout of
```

lsusb -v
```[COLOR=DarkSlateBlue]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
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
  iManufacturer           3 Linux 2.6.35-22-powerpc64-smp ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0001:02:0b.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         6400
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
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x05e3 Genesys Logic, Inc.
  idProduct          0x0608 USB-2.0 4-Port HUB
  bcdDevice            7.02
  iManufacturer           0 
  iProduct                1 USB2.0 Hub
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         6400
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
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
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x00e0
    Ganged power switching
    Ganged overcurrent protection
    TT think time 32 FS bits
    Port indicators
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

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
  iManufacturer           3 Linux 2.6.35-22-powerpc64-smp ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0001:02:0b.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         6400
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
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             5
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0503 highspeed power enable connect
   Port 5: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 004 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc52b Unifying Receiver
  bcdDevice           12.00
  iManufacturer           1 Logitech
  iProduct                2 USB Receiver
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength        21504
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          4 RQR12.00_B0017
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      59
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
        wMaxPacketSize     0x0800  2x 0 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
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
          wDescriptorLength     148
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0800  2x 0 bytes
        bInterval               2
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      98
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x2000  1x 0 bytes
        bInterval               2
Device Status:     0x0000
  (Bus Powered)

Bus 004 Device 003: ID 05ac:0205 Apple, Inc. Extended Keyboard [Mitsumi]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05ac Apple, Inc.
  idProduct          0x0205 Extended Keyboard [Mitsumi]
  bcdDevice            1.22
  iManufacturer           1 Mitsumi Electric
  iProduct                3 Apple Extended USB Keyboard
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength        15104
    bNumInterfaces          2
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
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode           13 International (ISO)
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      65
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
        wMaxPacketSize     0x0800  2x 0 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode           13 International (ISO)
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     110
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval             255
Device Status:     0x0000
  (Bus Powered)

Bus 004 Device 002: ID 05ac:1002 Apple, Inc. Extended Keyboard Hub [Mitsumi]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0         8
  idVendor           0x05ac Apple, Inc.
  idProduct          0x1002 Extended Keyboard Hub [Mitsumi]
  bcdDevice            1.22
  iManufacturer           1 Mitsumi Electric
  iProduct                2 Hub in Apple Extended USB Keyboard
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         6400
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
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0004
    Ganged power switching
    Compound device
    Ganged overcurrent protection
  bPwrOn2PwrGood       22 * 2 milli seconds
  bHubContrCurrent     50 milli Ampere
  DeviceRemovable    0x02
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0103 power enable connect
   Port 3: 0000.0100 power
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
  iManufacturer           3 Linux 2.6.35-22-powerpc64-smp ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0001:02:0b.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         6400
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
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect
   Port 3: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

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
  iManufacturer           3 Linux 2.6.35-22-powerpc64-smp ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0001:01:09.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         6400
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
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
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
  iManufacturer           3 Linux 2.6.35-22-powerpc64-smp ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0001:01:08.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         6400
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
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled
[COLOR=Black]

The problem is even worst than ever now with the keyboard coutting out after just a few seconds [/COLOR][/COLOR]:frown:

Oh and my gnome-settings-deamon seems to have cut out again. Heres the sys.log;

[COLOR=DarkSlateBlue]Apr 19 21:45:11 G5-ubuntu-10 cron[949]: (CRON) INFO (Running @reboot jobs)
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <error> [1303242311.761675] [nm-device-ethernet.c:729] real_update_permanent_hw_address(): (eth0): unable to read permanent MAC address (error 0)
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <info> (eth0): carrier is OFF
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <info> (eth0): new Ethernet device (driver: 'gem' ifindex: 2)
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <info> (eth0): now managed
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <info> (eth0): bringing up device.
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <info> (eth0): preparing device.
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <info> (eth0): deactivating device (reason: 2).
Apr 19 21:45:11 G5-ubuntu-10 kernel: [   12.803962] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0001:00/0001:00:06.0/0001:04:0f.0/net/eth0
Apr 19 21:45:11 G5-ubuntu-10 init: apport post-stop process (955) terminated with status 1
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Apr 19 21:45:11 G5-ubuntu-10 anacron[947]: Normal exit (0 jobs run)
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <info> modem-manager is now available
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <info> Trying to start the supplicant...
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <info> (wlan0): supplicant manager state:  down -> idle
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Apr 19 21:45:11 G5-ubuntu-10 NetworkManager[841]: <info> (wlan0): supplicant interface state:  starting -> ready
Apr 19 21:45:11 G5-ubuntu-10 pbbuttonsd: ERROR: The object '/dev/adb' doesn't exist.
Apr 19 21:45:11 G5-ubuntu-10 pbbuttonsd: WARNING: No backlight driver available - check your Kernel configuration.
Apr 19 21:45:11 G5-ubuntu-10 pbbuttonsd: ERROR: The object '/dev/adb' doesn't exist.
Apr 19 21:45:11 G5-ubuntu-10 kernel: [   12.882256] ioctl32(pbbuttonsd:963): Unknown cmd fd(10) cmd(40044201){t:'B';sz:4} arg(ffef730c) on /dev/pmu
Apr 19 21:45:12 G5-ubuntu-10 kernel: [   13.094460] RPC: Registered udp transport module.
Apr 19 21:45:12 G5-ubuntu-10 kernel: [   13.094465] RPC: Registered tcp transport module.
Apr 19 21:45:12 G5-ubuntu-10 kernel: [   13.094467] RPC: Registered tcp NFSv4.1 backchannel transport module.
Apr 19 21:45:12 G5-ubuntu-10 kernel: [   13.143737] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Apr 19 21:45:12 G5-ubuntu-10 kernel: [   13.198079] svc: failed to register lockdv1 RPC service (errno 97).
Apr 19 21:45:12 G5-ubuntu-10 kernel: [   13.200496] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Apr 19 21:45:12 G5-ubuntu-10 kernel: [   13.200866] NFSD: starting 90-second grace period
Apr 19 21:45:12 G5-ubuntu-10 dhclient: isc-dhclient-V3.1.3
Apr 19 21:45:12 G5-ubuntu-10 dhclient: isc-dhclient-V3.1.3
Apr 19 21:45:13 G5-ubuntu-10 gdm-binary[1130]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 19 21:45:13 G5-ubuntu-10 kernel: [   14.750211] lp: driver loaded but no devices found
Apr 19 21:45:13 G5-ubuntu-10 udev-configure-printer: add /module/lp
Apr 19 21:45:13 G5-ubuntu-10 udev-configure-printer: Failed to get parent
Apr 19 21:45:13 G5-ubuntu-10 kernel: [   14.763164] ppdev: user-space parallel port driver
Apr 19 21:45:13 G5-ubuntu-10 gdm-binary[1130]: WARNING: Unable to find users: no seat-id found
Apr 19 21:45:13 G5-ubuntu-10 gdm-simple-slave[1217]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 19 21:45:13 G5-ubuntu-10 kernel: [   15.017118] [drm] Initialized drm 1.1.0 20060810
Apr 19 21:45:14 G5-ubuntu-10 kernel: [   15.101084] [drm] radeon defaulting to kernel modesetting.
Apr 19 21:45:14 G5-ubuntu-10 kernel: [   15.101090] [drm] radeon kernel modesetting enabled.
Apr 19 21:45:16 G5-ubuntu-10 gdm-session-worker[1276]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 19 21:45:16 G5-ubuntu-10 rtkit-daemon[1284]: Successfully called chroot.
Apr 19 21:45:16 G5-ubuntu-10 rtkit-daemon[1284]: Successfully dropped privileges.
Apr 19 21:45:16 G5-ubuntu-10 rtkit-daemon[1284]: Successfully limited resources.
Apr 19 21:45:16 G5-ubuntu-10 rtkit-daemon[1284]: Running.
Apr 19 21:45:16 G5-ubuntu-10 rtkit-daemon[1284]: Watchdog thread running.
Apr 19 21:45:16 G5-ubuntu-10 rtkit-daemon[1284]: Canary thread running.
Apr 19 21:45:16 G5-ubuntu-10 polkitd[1288]: started daemon version 0.96 using authority implementation `local' version `0.96'
Apr 19 21:45:16 G5-ubuntu-10 kernel: [   17.642625] ioctl32(perl:1295): Unknown cmd fd(3) cmd(40044205){t:'B';sz:4} arg(1012f5d0) on /dev/pmu
Apr 19 21:45:16 G5-ubuntu-10 rtkit-daemon[1284]: Successfully made thread 1280 of process 1280 (n/a) owned by '113' high priority at nice level -11.
Apr 19 21:45:16 G5-ubuntu-10 rtkit-daemon[1284]: Supervising 1 threads of 1 processes of 1 users.
Apr 19 21:45:16 G5-ubuntu-10 kernel: [   17.711062] ioctl32(perl:1305): Unknown cmd fd(3) cmd(40044205){t:'B';sz:4} arg(106ea5d0) on /dev/pmu
Apr 19 21:45:16 G5-ubuntu-10 kernel: [   17.860275] ioctl32(perl:1317): Unknown cmd fd(3) cmd(40044205){t:'B';sz:4} arg(107756c0) on /dev/pmu
Apr 19 21:45:16 G5-ubuntu-10 rtkit-daemon[1284]: Successfully made thread 1316 of process 1280 (n/a) owned by '113' RT at priority 5.
Apr 19 21:45:16 G5-ubuntu-10 rtkit-daemon[1284]: Supervising 2 threads of 1 processes of 1 users.
Apr 19 21:45:16 G5-ubuntu-10 rtkit-daemon[1284]: Successfully made thread 1319 of process 1280 (n/a) owned by '113' RT at priority 5.
Apr 19 21:45:16 G5-ubuntu-10 rtkit-daemon[1284]: Supervising 3 threads of 1 processes of 1 users.
Apr 19 21:45:17 G5-ubuntu-10 gdm-simple-greeter[1273]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Apr 19 21:45:17 G5-ubuntu-10 anacron[1374]: Anacron 2.3 started on 2011-04-19
Apr 19 21:45:17 G5-ubuntu-10 anacron[1374]: Normal exit (0 jobs run)
Apr 19 21:45:17 G5-ubuntu-10 kernel: [   18.446795] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,commit=0
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:20 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:20 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:20 G5-ubuntu-10 dhclient: 
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Listening on LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Sending on   LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:20 G5-ubuntu-10 kernel: [   21.369169] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Apr 19 21:45:20 G5-ubuntu-10 kernel: [   21.439934] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:20 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:20 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:20 G5-ubuntu-10 dhclient: 
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Listening on LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Sending on   LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:20 G5-ubuntu-10 dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Apr 19 21:45:20 G5-ubuntu-10 dhclient: send_packet: Network is unreachable
Apr 19 21:45:20 G5-ubuntu-10 dhclient: send_packet: please consult README file regarding broadcast address.
Apr 19 21:45:20 G5-ubuntu-10 kernel: [   21.637140] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:20 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:20 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:20 G5-ubuntu-10 dhclient: 
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Listening on LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Sending on   LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:20 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:20 G5-ubuntu-10 kernel: [   21.905179] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Apr 19 21:45:20 G5-ubuntu-10 kernel: [   21.967340] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 19 21:45:29 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:29 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:29 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:29 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:29 G5-ubuntu-10 dhclient: 
Apr 19 21:45:29 G5-ubuntu-10 dhclient: Listening on LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:29 G5-ubuntu-10 dhclient: Sending on   LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:29 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:29 G5-ubuntu-10 kernel: [   30.710147] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Apr 19 21:45:29 G5-ubuntu-10 kernel: [   30.786713] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 19 21:45:29 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:29 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:29 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:29 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:29 G5-ubuntu-10 dhclient: 
Apr 19 21:45:29 G5-ubuntu-10 dhclient: Listening on LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:29 G5-ubuntu-10 dhclient: Sending on   LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:29 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:29 G5-ubuntu-10 dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Apr 19 21:45:29 G5-ubuntu-10 dhclient: send_packet: Network is unreachable
Apr 19 21:45:29 G5-ubuntu-10 dhclient: send_packet: please consult README file regarding broadcast address.
Apr 19 21:45:29 G5-ubuntu-10 kernel: [   30.969295] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 19 21:45:30 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:30 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:30 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:30 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:30 G5-ubuntu-10 dhclient: 
Apr 19 21:45:30 G5-ubuntu-10 dhclient: Listening on LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:30 G5-ubuntu-10 dhclient: Sending on   LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:30 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:30 G5-ubuntu-10 kernel: [   31.249147] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Apr 19 21:45:30 G5-ubuntu-10 kernel: [   31.311344] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 19 21:45:30 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:30 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:30 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:30 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:30 G5-ubuntu-10 dhclient: 
Apr 19 21:45:30 G5-ubuntu-10 dhclient: Listening on LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:30 G5-ubuntu-10 dhclient: Sending on   LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:30 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:31 G5-ubuntu-10 kernel: [   32.261188] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Apr 19 21:45:31 G5-ubuntu-10 kernel: [   32.331831] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 19 21:45:31 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:31 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:31 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:31 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:31 G5-ubuntu-10 dhclient: 
Apr 19 21:45:31 G5-ubuntu-10 dhclient: Listening on LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:31 G5-ubuntu-10 dhclient: Sending on   LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:31 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:31 G5-ubuntu-10 dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Apr 19 21:45:31 G5-ubuntu-10 dhclient: send_packet: Network is unreachable
Apr 19 21:45:31 G5-ubuntu-10 dhclient: send_packet: please consult README file regarding broadcast address.
Apr 19 21:45:31 G5-ubuntu-10 kernel: [   32.517592] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 19 21:45:39 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:39 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:39 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:39 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:39 G5-ubuntu-10 dhclient: 
Apr 19 21:45:39 G5-ubuntu-10 dhclient: Listening on LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:39 G5-ubuntu-10 dhclient: Sending on   LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:39 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:39 G5-ubuntu-10 kernel: [   40.937126] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Apr 19 21:45:39 G5-ubuntu-10 kernel: [   41.007763] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 19 21:45:39 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:39 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:39 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:39 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:39 G5-ubuntu-10 dhclient: 
Apr 19 21:45:39 G5-ubuntu-10 dhclient: Listening on LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:39 G5-ubuntu-10 dhclient: Sending on   LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:39 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:40 G5-ubuntu-10 dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Apr 19 21:45:40 G5-ubuntu-10 dhclient: send_packet: Network is unreachable
Apr 19 21:45:40 G5-ubuntu-10 dhclient: send_packet: please consult README file regarding broadcast address.
Apr 19 21:45:40 G5-ubuntu-10 kernel: [   41.189125] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 19 21:45:40 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:40 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:40 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:40 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:40 G5-ubuntu-10 dhclient: 
Apr 19 21:45:40 G5-ubuntu-10 dhclient: Listening on LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:40 G5-ubuntu-10 dhclient: Sending on   LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:40 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:40 G5-ubuntu-10 kernel: [   41.445124] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Apr 19 21:45:40 G5-ubuntu-10 kernel: [   41.522883] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 19 21:45:41 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:41 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:41 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:41 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:41 G5-ubuntu-10 dhclient: 
Apr 19 21:45:41 G5-ubuntu-10 dhclient: Listening on LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:41 G5-ubuntu-10 dhclient: Sending on   LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:41 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:41 G5-ubuntu-10 kernel: [   42.473117] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Apr 19 21:45:41 G5-ubuntu-10 kernel: [   42.543793] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 19 21:45:41 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:41 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:41 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:41 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:41 G5-ubuntu-10 dhclient: 
Apr 19 21:45:41 G5-ubuntu-10 dhclient: Listening on LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:41 G5-ubuntu-10 dhclient: Sending on   LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:41 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:41 G5-ubuntu-10 dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Apr 19 21:45:41 G5-ubuntu-10 dhclient: send_packet: Network is unreachable
Apr 19 21:45:41 G5-ubuntu-10 dhclient: send_packet: please consult README file regarding broadcast address.
Apr 19 21:45:41 G5-ubuntu-10 kernel: [   42.737379] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 19 21:45:49 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:49 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:49 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:49 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:49 G5-ubuntu-10 dhclient: 
Apr 19 21:45:49 G5-ubuntu-10 dhclient: Listening on LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:49 G5-ubuntu-10 dhclient: Sending on   LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:49 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:49 G5-ubuntu-10 kernel: [   50.837112] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Apr 19 21:45:49 G5-ubuntu-10 kernel: [   50.907738] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 19 21:45:49 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:49 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:49 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:49 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:49 G5-ubuntu-10 dhclient: 
Apr 19 21:45:49 G5-ubuntu-10 dhclient: Listening on LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:49 G5-ubuntu-10 dhclient: Sending on   LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:49 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:49 G5-ubuntu-10 dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Apr 19 21:45:49 G5-ubuntu-10 dhclient: send_packet: Network is unreachable
Apr 19 21:45:49 G5-ubuntu-10 dhclient: send_packet: please consult README file regarding broadcast address.
Apr 19 21:45:50 G5-ubuntu-10 kernel: [   51.081429] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 19 21:45:50 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:50 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:50 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:50 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:50 G5-ubuntu-10 dhclient: 
Apr 19 21:45:50 G5-ubuntu-10 dhclient: Listening on LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:50 G5-ubuntu-10 dhclient: Sending on   LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:50 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:50 G5-ubuntu-10 kernel: [   51.341100] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Apr 19 21:45:50 G5-ubuntu-10 kernel: [   51.410873] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 19 21:45:51 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:51 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:51 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:51 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:51 G5-ubuntu-10 dhclient: 
Apr 19 21:45:51 G5-ubuntu-10 dhclient: Listening on LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:51 G5-ubuntu-10 dhclient: Sending on   LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:51 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:51 G5-ubuntu-10 kernel: [   52.365093] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Apr 19 21:45:51 G5-ubuntu-10 kernel: [   52.435776] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 19 21:45:51 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:51 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:51 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:51 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:51 G5-ubuntu-10 dhclient: 
Apr 19 21:45:51 G5-ubuntu-10 dhclient: Listening on LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:51 G5-ubuntu-10 dhclient: Sending on   LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:51 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:51 G5-ubuntu-10 dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Apr 19 21:45:51 G5-ubuntu-10 dhclient: send_packet: Network is unreachable
Apr 19 21:45:51 G5-ubuntu-10 dhclient: send_packet: please consult README file regarding broadcast address.
Apr 19 21:45:51 G5-ubuntu-10 kernel: [   52.613429] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 19 21:45:57 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:57 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:57 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:57 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:57 G5-ubuntu-10 dhclient: 
Apr 19 21:45:57 G5-ubuntu-10 dhclient: Listening on LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:57 G5-ubuntu-10 dhclient: Sending on   LPF/wlan0/00:11:24:93:ce:d5
Apr 19 21:45:57 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:57 G5-ubuntu-10 kernel: [   58.349081] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Apr 19 21:45:57 G5-ubuntu-10 kernel: [   58.419721] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 19 21:45:57 G5-ubuntu-10 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 19 21:45:57 G5-ubuntu-10 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 19 21:45:57 G5-ubuntu-10 dhclient: All rights reserved.
Apr 19 21:45:57 G5-ubuntu-10 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 19 21:45:57 G5-ubuntu-10 dhclient: 
Apr 19 21:45:57 G5-ubuntu-10 dhclient: Listening on LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:57 G5-ubuntu-10 dhclient: Sending on   LPF/eth0/00:14:51:11:49:50
Apr 19 21:45:57 G5-ubuntu-10 dhclient: Sending on   Socket/fallback
Apr 19 21:45:57 G5-ubuntu-10 dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Apr 19 21:45:57 G5-ubuntu-10 dhclient: send_packet: Network is unreachable
Apr 19 21:45:57 G5-ubuntu-10 dhclient: send_packet: please consult README file regarding broadcast address.
Apr 19 21:45:57 G5-ubuntu-10 kernel: [   58.609224] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 19 21:46:12 G5-ubuntu-10 kernel: [   73.628306] ondemand governor failed, too long transition latency of HW, fallback to performance governor
Apr 19 21:46:12 G5-ubuntu-10 kernel: [   73.628376] ondemand governor failed, too long transition latency of HW, fallback to performance governor
Apr 19 21:46:17 G5-ubuntu-10 gdm-session-worker[1276]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 19 21:46:39 G5-ubuntu-10 gdm-session-worker[1672]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 19 21:46:41 G5-ubuntu-10 gdm-session-worker[1672]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 19 21:46:51 G5-ubuntu-10 gdm-session-worker[1683]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 19 21:46:53 G5-ubuntu-10 gdm-session-worker[1683]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 19 21:46:55 G5-ubuntu-10 gdm-session-worker[1689]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 19 21:46:56 G5-ubuntu-10 gdm-session-worker[1689]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 19 21:47:06 G5-ubuntu-10 kernel: [  127.815513] usb 4-2: USB disconnect, address 2
Apr 19 21:47:06 G5-ubuntu-10 kernel: [  127.815518] usb 4-2.1: USB disconnect, address 3
Apr 19 21:47:06 G5-ubuntu-10 kernel: [  127.885245] usb 4-2.2: USB disconnect, address 4
Apr 19 21:47:09 G5-ubuntu-10 kernel: [  130.481582] usb 1-4.2: new full speed USB device using ehci_hcd and address 4
Apr 19 21:47:09 G5-ubuntu-10 kernel: [  130.575002] hub 1-4.2:1.0: USB hub found
Apr 19 21:47:09 G5-ubuntu-10 kernel: [  130.575207] hub 1-4.2:1.0: 3 ports detected
Apr 19 21:47:09 G5-ubuntu-10 kernel: [  130.845057] usb 1-4.2.1: new full speed USB device using ehci_hcd and address 5
Apr 19 21:47:09 G5-ubuntu-10 kernel: [  130.941007] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0001:00/0001:00:04.0/0001:02:0b.2/usb1/1-4/1-4.2/1-4.2.1/1-4.2.1:1.0/input/input6
Apr 19 21:47:09 G5-ubuntu-10 kernel: [  130.941368] generic-usb 0003:05AC:0205.0006: input,hidraw0: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0001:02:0b.2-4.2.1/input0
Apr 19 21:47:09 G5-ubuntu-10 kernel: [  130.943317] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0001:00/0001:00:04.0/0001:02:0b.2/usb1/1-4/1-4.2/1-4.2.1/1-4.2.1:1.1/input/input7
Apr 19 21:47:09 G5-ubuntu-10 kernel: [  130.943661] generic-usb 0003:05AC:0205.0007: input,hidraw1: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0001:02:0b.2-4.2.1/input1
Apr 19 21:47:09 G5-ubuntu-10 kernel: [  131.013077] usb 1-4.2.2: new full speed USB device using ehci_hcd and address 6
Apr 19 21:47:10 G5-ubuntu-10 kernel: [  131.111061] input: Logitech USB Receiver as /devices/pci0001:00/0001:00:04.0/0001:02:0b.2/usb1/1-4/1-4.2/1-4.2.2/1-4.2.2:1.0/input/input8
Apr 19 21:47:10 G5-ubuntu-10 kernel: [  131.111288] generic-usb 0003:046D:C52B.0008: input,hidraw2: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0001:02:0b.2-4.2.2/input0
Apr 19 21:47:10 G5-ubuntu-10 kernel: [  131.114355] input: Logitech USB Receiver as /devices/pci0001:00/0001:00:04.0/0001:02:0b.2/usb1/1-4/1-4.2/1-4.2.2/1-4.2.2:1.1/input/input9
Apr 19 21:47:10 G5-ubuntu-10 kernel: [  131.114686] generic-usb 0003:046D:C52B.0009: input,hiddev96,hidraw3: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0001:02:0b.2-4.2.2/input1
Apr 19 21:47:10 G5-ubuntu-10 kernel: [  131.124956] generic-usb 0003:046D:C52B.000A: hiddev97,hidraw4: USB HID v1.11 Device [Logitech USB Receiver] on usb-0001:02:0b.2-4.2.2/input2
Apr 19 21:47:15 G5-ubuntu-10 NetworkManager[841]: <error> [1303242435.814525] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Apr 19 21:47:15 G5-ubuntu-10 NetworkManager[841]: <error> [1303242435.859814] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name


[COLOR=Black]Thanks

Dc
[/COLOR][/COLOR] [COLOR=DarkSlateBlue][COLOR=Black]
[/COLOR][/COLOR]

---

### Post by 1984dc on 2011-04-20
Bump

---

### Post by 1984dc on 2011-04-21
Bump

---

### Post by 1984dc on 2011-04-22
Bump

---

### Post by 1984dc on 2011-04-25
Fed up of bumpiong this, i am going to make a new post just about the keyboard issues (as the grey theme problem is pretty much fixed and not so disibilitating).

---

### Post by jasononlinux on 2011-04-26
getting the same issue w/ the theme, but no keyboard issues thus far.

---

### Post by 1984dc on 2011-04-27
Try running

```
gnome-settings-deamon
```

From the terminal and that should fix it (though i am not sure how permanently).

;)

---

### Post by 1984dc on 2011-04-27
Tried resetting my xorg.conf but that didn´t fix it :(

---

### Post by 1984dc on 2011-04-27
[COLOR=Navy]Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "record"
    Load  "glx"
    Load  "dbe"
    Load  "dri2"
    Load  "extmod"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "CustomEDID"             # [<str>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "MacModel"               # <str>
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
        #Option     "NewPLL"                 # [<bool>]
        #Option     "ZaphodHeads"            # <str>
    Option      "Reverse DDC"        "on"
    Identifier  "Card0"
    Driver      "radeon"
    BusID       "PCI:240:16:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

[/COLOR]

---

### Post by 1984dc on 2011-04-28
Think it is the xorg.conf Here´s the print out of the xorg.0.log

[COLOR=Blue]www.ubuntu.com/support) 
[    14.781] Current version of pixman: 0.18.4
[    14.781]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    14.781] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.782] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 27 20:50:47 2011
[    14.782] (==) Using config file: "/etc/X11/xorg.conf"
[    14.782] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[COLOR=Red][    14.783] Data incomplete in file /etc/X11/xorg.conf
    Undefined InputDevice "Keyboard0" referenced by ServerLayout "X.org Configured".[/COLOR]
[    14.783] (EE) Problem parsing the config file
[    14.783] (EE) Error parsing the config file
[    14.783] 
Fatal server error:
[    14.783] no screens found
[    14.783] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    14.783] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    14.783] 
[    14.783]  ddxSigGiveUp: Closing log[/COLOR]

[COLOR=Black]Its random though as it worked fine when i created the original xorg.conf after installation :confused:[/COLOR]

---

### Post by 1984dc on 2011-04-29
Bump

---

### Post by Sam G on 2011-04-29
> **1984dc said:**
> Try running

```
gnome-settings-deamon
```

From the terminal and that should fix it (though i am not sure how permanently).

;)

Not thread hijacking, but saying thanks for the terminal command and sharing my similar issue. :)

I have a similar problem on 11.04. Starting with a fresh install of 11.04 (32-bit) in VirtualBox v4.0.6. r71416 on a Win7 (32-bit) host, I boot up the first time and I have the proper theme. However, on the next boot I have a completely different theme. I did not use any keyboard commands/shortcuts, as described in the OP.

1st boot:
[IMG]http://i.imgur.com/XJVsR.png[/IMG]

2+ boots:
[IMG]http://i.imgur.com/AUatM.png[/IMG]

Changing the theme back does change the windows, but not the icons and taskbar for some reason. I then found this thread and tried the above command (fixed the type though) and it is now back to normal for this session.

In terminal:
```
sudo gnome-settings-d**ae**mon
```

I hope this get's resolved, because it is really annoying.

---

### Post by 1984dc on 2011-05-02
Hi Sam thanks for your post, I'm glad I am not the only one in this particular boat. I myself have two completely different computers (ppc G5 power mac and a Compaq minipc 311c they literally could not be more different) and i had the same issue on both of the machines, and i haven't found a proper fix (this only happens in 10.10). Thanks for the fix of the typo I am not a very accurate speller at the best of times :)
 
The keyboard issue is new though and I'm pretty sure that it is un related so I will definitely make a new post for that (when I get a moment to myself!).
 
All the best.
 
DC

---

### Post by 1984dc on 2011-05-02
Here is a link to the new thread just regarding the keyboard problems (as they are a seperate subject):

[[COLOR=DeepSkyBlue]**Here**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=10757661#post10757661")

---

### Post by Mckormick on 2011-05-05
Hi all 

I've just started getting the grey screen problem on 2 separate computers running 10.10 Desktop:

- Dell XPS M1330 with integrated Intel x3100 graphics
- Toshiba Libretto U100 with integrated Intel 82852/855GM graphics

It seemed to start when the Natty dist upgrade became available although I haven't actually upgraded either yet.

If I just open the appearance manager (don't change anything) it reverts back to my chosen theme but only temporarily.

Any ideas or is there a bug report for this?

cheers

---

