---
title: "Trying to get one of two wireless adapters working"
date: 2011-09-29
forum: General Help
---

### Post by SirSilvia on 2011-09-29
I have a HP Pavilion dv2000 laptop had a bad hard drive but was running Ubuntu 11.04 from the disk, and the wireless worked fine. After installing a new hard drive and installing the OS the wireless adapter will not enable. wireless switch is turned on and everything as well. I even disassembled the laptop to see if the wireless switch was broken.

I've checked out the following support sites and forum posts for the built in adapter.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers)
[http://ubuntuforums.org/showthread.php?t=859481](http://ubuntuforums.org/showthread.php?t=859481)
[http://ubuntuforums.org/showthread.php?t=1453806](http://ubuntuforums.org/showthread.php?t=1453806)

Working on this one next.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

That is for the built in one. I've bought an additional one, the Netgear G54/N150 Wireless USB Micro Adapter Model: WNA1000M-100ENS

**As you can see below, the built in adapter has drivers installed but unable to enable it. **

> sirsilvia@Mobile-Lulz:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:16:D3:AB:1D:FF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             unavailable
  Default:           no
  HW Address:        00:1B:77:AE:FD:7E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 




**And the Netgear is not accpeting the drivers using the NDISwrapper. The laptop however recognizes it**

> sirsilvia@Mobile-Lulz:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 002: ID 0846:9041 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I would like to get the built in one enabled or the Netgear one installed, either way, I want to stop having to plug direct with a cat5

-Thanks

and btw I'm mainly a causal tinkerer so I am a novice but willing to learn.

---

