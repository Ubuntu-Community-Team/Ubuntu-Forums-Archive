---
title: "Cowon D2 MP3 player wont mount"
date: 2009-11-18
forum: General Help
---

### Post by Hawk__0 on 2009-11-18
It hasn't work with ubuntu since 7.10 (I think).  Before that it was fine.  When I plug it in I can see it with lsusb:

```
steve@steves-desktop:~$ sudo lsusb
Bus 002 Device 002: ID 2101:020f ActionStar 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0e21:0801 Cowon Systems, Inc. Cowon D2 (MTP mode)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
steve@steves-desktop:~$ 

```

The verbose output:

```
steve@steves-desktop:~$ sudo lsusb -v 

Bus 002 Device 002: ID 2101:020f ActionStar 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x2101 ActionStar
  idProduct          0x020f 
  bcdDevice            0.01
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
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
      ** UNRECOGNIZED:  09 21 01 01 00 01 22 3f 00
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
      ** UNRECOGNIZED:  09 21 01 01 00 01 22 48 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0002
  (Bus Powered)
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
  iManufacturer           3 Linux 2.6.31-14-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:0b.0
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
  bLength              11
  bDescriptorType      41
  nNbrPorts             8
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0303 lowspeed power enable connect
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 004: ID 0e21:0801 Cowon Systems, Inc. Cowon D2 (MTP mode)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0e21 Cowon Systems, Inc.
  idProduct          0x0801 Cowon D2 (MTP mode)
  bcdDevice            2.51
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
can't get device qualifier: Connection timed out
can't get debug descriptor: Connection timed out
cannot read device status, Connection timed out (110)

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
  iManufacturer           3 Linux 2.6.31-14-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:0b.1
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
  bLength              11
  bDescriptorType      41
  nNbrPorts             8
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0503 highspeed power enable connect
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

```

How can I get it to recognize it?  It's just an MP3 player with flash memory inside it..

---

### Post by Hawk__0 on 2009-11-18
ummmmm wtf? Amarok picks it up... but it doesn't show in my panel...

---

### Post by l_synapse_l on 2009-11-18
I have one too. Let me check it and get back to you.

---

### Post by l_synapse_l on 2009-11-18
> **l_synapse_l said:**
> I have one too. Let me check it and get back to you.

Mounts perfectly for me. I am on Karmic Koala 9.10. Check out the screenshots below

[http://profile.imageshack.us/user/acoustique/images/detail/#684/cowond2mountsshot.png](http://profile.imageshack.us/user/acoustique/images/detail/#684/cowond2mountsshot.png)

[http://img684.imageshack.us/img684/5346/screenshotd2filebrowser.png](http://img684.imageshack.us/img684/5346/screenshotd2filebrowser.png)

Edit : Updated link

---

### Post by Hawk__0 on 2009-11-18
Weird.  Mine doesn't pop up at ALL.  but the files are readable by Amarok..

I just checked and it randomly mounted itself.  I never got a popup though... this is odd.

---

### Post by Hawk__0 on 2009-11-20
OK WTF. 

SO frustrated with this!  Once again amarok has picked it up.  I plugged it in about 10 minutes ago, and STILL no visible mount.  the mount and mnt directory are empty other than the usual directories (cdrom, floppy, etc).  I even checked those folders.  nothing.  the mount command is useless:

```
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/steve/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=steve)

```

I'm listening to music off it now... in amarok... like wtf!?

---

### Post by SuperSonic4 on 2009-11-20
What is the firmware version?

Mine works perfectly with firmware 2.59, dolphin sees it. Have you checked in Settings---> System --> USB settings to see if it's MSC? [on the D2]

---

### Post by Hawk__0 on 2009-11-20
Thanks you for the reply.  I will check this and repost later.  The D2 showed up after I rebooted (and left it plugged in...).  Strange? Yes.  Can you direct me where to get the firmware update? I think mine is 2.4X

Edit:

I have 2.51

---

### Post by SuperSonic4 on 2009-11-21
Perhaps it's your firmware because mine did not work with version 2.2 until I updated to 2.59

Amarok recognises MTP devices but to my knowledge file managers do not

---

### Post by Z06Gal on 2009-11-22
> **l_synapse_l said:**
> Mounts perfectly for me. I am on Karmic Koala 9.10. Check out the screenshots below

[http://profile.imageshack.us/user/acoustique/images/detail/#684/cowond2mountsshot.png](http://profile.imageshack.us/user/acoustique/images/detail/#684/cowond2mountsshot.png)

[http://img684.imageshack.us/img684/5346/screenshotd2filebrowser.png](http://img684.imageshack.us/img684/5346/screenshotd2filebrowser.png)

Edit : Updated link

 
I just got my d2+ last week and had no problems putting my music on it but I am having problems putting a video on it.  I ripped the dvd to my hd and used avidemux to encode without any issues.  It shows the movie transferring to the player but when I turn it on it isn't there.  Is there some sort of setting on the player I need to do?  Thanks. 

Robin

---

### Post by Hawk__0 on 2009-11-23
Today it seemed to connect fine... I updated the firmware and have not had issues since.  I got the firmware from here (2.59): [http://support.cowonamerica.com/supportcentral/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=355](http://support.cowonamerica.com/supportcentral/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=355)

---

