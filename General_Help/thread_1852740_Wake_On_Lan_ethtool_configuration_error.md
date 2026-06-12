---
title: "Wake On Lan ethtool configuration error"
date: 2011-09-30
forum: General Help
---

### Post by Chowarmaan on 2011-09-30
I have set my Wake on Lan on for Windows and it works well.  I am trying the same thing on a Ubuntu machine at home, but the help online gives me errors when I try it.  I can ethtool errors following the instructions.  I have enabled the Wake on Lan in my BIOS.

~$ sudo ethtool eth1
Settings for eth1:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 8
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: d
    Wake-on: d
    Current message level: 0x00000001 (1)
                   drv
    Link detected: yes

This appears to have my support disabled.  I am checking that again, but I get errors using the -s setting of ehttool.

~$ sudo ethtool --change eth1 wol bg
Cannot set new wake-on-lan settings: Invalid argument
  not setting wol

Not sure what is wrong aside from possibly the Supports Wake-on: d?

Any help or suggestions would be appreciated.  Thanks in advance.

---

### Post by papibe on 2011-09-30
Have you tried just setting one option at a time?

For example:
```
$ sudo ethtool -s eth1 wol g
```
Regards.

---

