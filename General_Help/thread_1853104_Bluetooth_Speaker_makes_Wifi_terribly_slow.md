---
title: "Bluetooth Speaker makes Wifi terribly slow?"
date: 2011-10-01
forum: General Help
---

### Post by vickoxy on 2011-10-01
Hi,
i had lot of problem with making my Sony Ericsson MBS-100 Bluetooth Speaker working with Lubuntu 11.04 and Shuttle XS35GTv2.
I found some solution:
[http://ubuntuforums.org/showthread.php?t=1852103](http://ubuntuforums.org/showthread.php?t=1852103)


But, i have another problem. If my Sony Ericsson MBS-100 Bluetooth Speaker is connected with computer, wifi is terribly slow-actually it can not load anything. So, if i watch some Youtube clip, i have to load music and after that i connect the box to hear it. Does anyone have any idea what to do?

---

### Post by Shazaam on 2011-10-01
Two things from two wiki pages...

Wifi-
```
Additionally, other devices use the 2.4 GHz band: microwave ovens, ISM band devices, security cameras, ZigBee devices, Bluetooth devices and (in some countries) Amateur radio, video senders, cordless phones and baby monitors, all of which can cause significant additional interference.
```

Bluetooth-
```
Bluetooth is a proprietary open wireless technology standard for exchanging data over short distances (using short wavelength radio transmissions in the ISM band from 2400-2480 MHz) from fixed and mobile devices, creating personal area networks (PANs) with high levels of security
```

Might be interference? I don't know for sure as I have neither bluetooth nor wifi.

---

### Post by cptrohn on 2011-10-01
First thing I thought of was that they were broadcasting on the same channel....  I would look in my routers settings and see if you can change the channel your WiFi is broadcasting with...

---

### Post by vickoxy on 2011-10-01
Well, how can i change the channel in ubuntu? Really no idea.
Or how to see what channel uses Bluetooth and what Wifi?

---

### Post by vickoxy on 2011-10-02
I found channels to be changed in web browser (192.168.1.1), but no matter what channel (1-13) i took, wifi connection get terribly slow as soon as i connect bluetooth speaker. Any idea?
This is channel list:
> linux@linux:~$ sdptool browse
Inquiring ...
Browsing C8:97:9F:9D:75:3C ...
Service Name: AVRCP Target
Service Description: Audio Video Remote Control
Service Provider: Symbian Software Ltd.
Service RecHandle: 0x10000
Service Class ID List:
  "AV Remote Target" (0x110c)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x102
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0103

Service RecHandle: 0x10001
Service Class ID List:
  UUID 128: 00005557-0000-1000-8000-0002ee000001
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1

Service Name: PnP Information
Service RecHandle: 0x10002
Service Class ID List:
  "PnP Information" (0x1200)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100

Service Name: OBEX Object Push
Service RecHandle: 0x10004
Service Class ID List:
  "OBEX Object Push" (0x1105)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 2
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "OBEX Object Push" (0x1105)
    Version: 0x0100

Service Name: SIM Access
Service RecHandle: 0x10005
Service Class ID List:
  "SIM Access" (0x112d)
  "Generic Telephony" (0x1204)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 21
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "SIM Access" (0x112d)
    Version: 0x0101

Service Name: Imaging
Service RecHandle: 0x10006
Service Class ID List:
  "Imaging Responder" (0x111b)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 3
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Imaging" (0x111a)
    Version: 0x0100

Service Name: SyncMLClient
Service RecHandle: 0x10007
Service Class ID List:
  UUID 128: 00000002-0000-1000-8000-0002ee000002
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 4
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00000002-0000-1000-8000-0002ee000002)
    Version: 0x0100

Service Name: Phonebook access PSE
Service Provider: Symbian Software Ltd
Service RecHandle: 0x10008
Service Class ID List:
  "Phonebook Access - PSE" (0x112f)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 5
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Phonebook Access" (0x1130)
    Version: 0x0100

Service Name: OBEX File Transfer
Service RecHandle: 0x10009
Service Class ID List:
  "OBEX File Transfer" (0x1106)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 6
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "OBEX File Transfer" (0x1106)
    Version: 0x0100

Service Name: Hands-Free Audio Gateway
Service RecHandle: 0x1000a
Service Class ID List:
  "Handsfree Audio Gateway" (0x111f)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 7
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Handsfree" (0x111e)
    Version: 0x0105

Service Name: Headset Audio Gateway
Service RecHandle: 0x1000b
Service Class ID List:
  "Headset Audio Gateway" (0x1112)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 8
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Headset" (0x1108)
    Version: 0x0100

Service Name: Audio Source
Service RecHandle: 0x1000c
Service Class ID List:
  "Audio Source" (0x110a)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x100
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0100

Service Name: AVRCP Controller
Service Description: Audio Video Remote Control
Service Provider: Symbian Software Ltd.
Service RecHandle: 0x1000d
Service Class ID List:
  "AV Remote" (0x110e)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x102
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0103

Service Name: Nokia OBEX PC Suite Services
Service RecHandle: 0x1000e
Service Class ID List:
  UUID 128: 00005005-0000-1000-8000-0002ee000001
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 9
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00005005-0000-1000-8000-0002ee000001)
    Version: 0x0100

Service Name: Nokia SyncML Server
Service RecHandle: 0x10010
Service Class ID List:
  UUID 128: 00005601-0000-1000-8000-0002ee000001
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 10
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00005601-0000-1000-8000-0002ee000001)
    Version: 0x0100

Service Name: Dial-Up Networking
Service RecHandle: 0x10012
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 22
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100


EDIT 1: just to confirm that i have no such problems with dell mini 9 and Lubuntu 11.04 there.
EDIT 2: if i hear mp3 music in vlc or audacious everything works just fine. But as soon as i open web browser and wifi is active, i have lots of distortion hearing music-so, it seems there is channel conflict, but, as said, i tried all wlan channels and nothing changes... Is there any way to change bluetooth device channel?

---

