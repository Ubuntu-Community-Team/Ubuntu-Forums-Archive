---
title: "NexusS Access SIM for LOCAL Sync Contacts+send SMS from PC by Rooting or other means?"
date: 2011-06-08
forum: General Help
---

### Post by Ronok on 2011-06-08
Hi, 
Please Help 

From a (100%) **UBUNTU** 10.10 machine --> to a Samsung **Nexus S**: 
[SIZE="3"]Need Access to **SIM**, [/SIZE](not just the "USB Storage")
for:
[INDENT][LIST=1]
[*]**LOCAL Sync**hronization of Contacts & SMS with UBUNTU-PC and 
[*]the sending of **SMS** from UBUNTU-PC via USB through Cell Phone
[/LIST][/INDENT]
by **"Rooting"** the phone, or what other means ?
[SIZE="1"](please see below the "info" for what I have already tried)[/SIZE]

**[SIZE="3"]Hardware / Software INFO[/SIZE]**

**UBUNTU Machine**
[INDENT][LIST]
[*]M-Bord: P67A-GD65 (MS-7681) 	
[*]Socket: 1155
[*]Chipset: Intel P67
[*]Processor: 8x Intel Core i7-2600K CPU @ 3.40GH
[*]UBUNTU 10.10
[*]Linux: 2.6.35-28-generic-pae i686
[*]GNOME: 2.32.0
[/LIST][/INDENT]

**Samsung Nexus S Cell Phone**

[INDENT][LIST]
[*]Android version: 2.3.4
[*]Baseband version: 19020XXKD1
[*]Kernel version: 2.6.35.7-ge382d80   android-build@apa28#1
[*]Build number: GRJ22
[*]Network: T-Mobile
[*]Purchased at: Bestbuy
[*]Open source License: "Freetype Project License"
[*]Phone is: UNlocked (Confirmed can change SIM Card)
in FASTBOOT MODE
[*]Product Name: Herring
[*]HW Version: Rev 11
[*]BootLoader Version: 19020XXKA3
[*]LOCKED STATE: **LOCKED** ( Not "Rooted" )
[/LIST][/INDENT]

```
user@computer:~$ lsusb
ID **18d1:4e22** Google Inc.
```

```

user@computer:~$ **lsusb -v**

Bus 002 Device 006: ID **18d1:4e22** Google Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x18d1 Google Inc.
  idProduct          0x4e22 
  bcdDevice            2.27
  iManufacturer           1 Samsung
  iProduct                2 Nexus S
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           55
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              8 Mass Storage
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0a  EP 10 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass     66 
      bInterfaceProtocol      1 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x8b  EP 11 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0d  EP 13 OUT
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

```


I followed the instructions
[INDENT]["GUIDE" **Linux Ubuntu: Unlocking Bootloader / Rooting Nexus S**]("http://forum.xda-developers.com/showthread.php?t=883032")
from: [xda-developers]("http://forum.xda-developers.com/index.php")
was able to Download all the files, and did everything **but** got:
```
user@computer:~$ fastboot oem unlock
fastboot: command not found
```[/INDENT]

so I Read some more Links:
[INDENT][ubuntuforums: Android + Ubuntu. Works?]("http://ubuntuforums.org/showthread.php?t=1141097&page=8&highlight=nexus")
[ubuntuforums: Project: Off-line sync for Android]("http://ubuntuforums.org/showthread.php?t=1618443&page=4")
[Android (operating system)]("http://en.wikipedia.org/wiki/Android_%28operating_system%29")
[Nexus S @ wikipedia]("http://en.wikipedia.org/wiki/Nexus_S")
[Rooting (Android OS)]("http://en.wikipedia.org/wiki/Rooting_%28Android_OS%29")
[Android SDK]("http://developer.android.com/sdk/index.html")
[Developing applications for the Google's Android phone on Ubuntu 9.10]("http://www.futuredesktop.org/developing_android_apps_on_ubuntu.html")
[/INDENT]

**[SIZE="3"]My End Goal:[/SIZE]**
[INDENT]I use: [img]http://img.informer.com/icons/png/32/503/503000.png[/img]Unison File Synchronizer, Version 2.32.52
for a lot of tasks (Local to Local, USB & SSH) and it works very well
would like to use Unison for **LOCAL Synchronization** of Contacts & SMS
that is from the PC to the SIM Card (not just the "USB Storage")[/INDENT]

Also:

[INDENT]on the PC keyboard type out **Text Messages (SMS)** and 
Send Them (via the USB cable) to the Cell Phone, then
receve text SMS from the Phone to the PC in the same way

I was in the past on another UBUNTU Laptop able to use "Wammu" successfully Do this 
[img]http://ostatic.com/files/images/icon_wammu_image_17.png[/img]Wammu 0.33 (Wammu is a wxPython based GUI for Gammu.)
Running on Python 2.6.6
Using wxPython 2.8.11.0
Using python-gammu 1.27.92 and Gammu 1.27.92

as it stands now **None** of the Phone Managers I found can see the Phone
(all available through: Applications > Ubuntu Software Center)
(BitPim 1.0.7 - Debian)(gmobilemedia)(Phone Manager 0.65)(Xgnokii)(KMobile Tools 0.4.3.3 using KDE3.5.10)[/INDENT]

**[SIZE="3"]Conclusion:[/SIZE]**
[LIST]
[*]I Need help "Rooting" this Nexus S
[*]Stuck at **UBUNTU** Terminal: "fastboot: command not found" ( Why ? )
[/LIST]

Any Help Greatly Appreciated
**Thanks**
[URL="http://www.gongkuo.com/linuxcli.htm"]My < Linux > Command Line Interface Page
[SIZE="1"]http://www.gongkuo.com/linuxcli.htm[/SIZE][/URL]

---

