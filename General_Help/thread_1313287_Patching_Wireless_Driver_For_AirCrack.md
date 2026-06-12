---
title: "Patching Wireless Driver For AirCrack??"
date: 2009-11-03
forum: General Help
---

### Post by cooldawg on 2009-11-03
[CENTER]Hi, I'm currently having a problem trying to patch my wireless driver so I can use aircrack.
[LEFT]I am using a HP Pavillion dv6000 with Ubuntu 9.04, and my wireless card works great. I tried using this tutorial to patch my driver: [http://ubuntulinuxhelp.com/using-ubuntu-to-crack-wep/](http://ubuntulinuxhelp.com/using-ubuntu-to-crack-wep/)    
I don't know what's wrong. I thought I once tried looking up my chipset... I think that I found this: [http://madwifi-project.org/changeset/3772](http://madwifi-project.org/changeset/3772)

the tutorial shows ath0

when I run iwconfig this is what i get:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"***"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: ***   
          Bit Rate=2 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:*** [3]   Security mode:open
          Power Management:off
          Link Quality=82/100  Signal level:-49 dBm  Noise level=-102 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

Can anyone help me out? I appreciate if you took the time to read this. If I need to provide more details I can. 
[/LEFT]
[/CENTER]

---

### Post by cooldawg on 2009-11-03
one more thing when i run:
sudo lshw -C network 
i get:

```


         
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:86:e6:e0
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:e2:ae:d2:74
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.10.2 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c6:69:a5:76:dd:49
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by cooldawg on 2009-12-27
can anyone help?

I can't seem to inject packets... does this card support packet injection?


I did find this, but I'm unsure of what to do. 
[http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng)

---

### Post by stew721 on 2009-12-27
[http://forum.aircrack-ng.org](http://forum.aircrack-ng.org)

---

### Post by cooldawg on 2009-12-27
> **stew721 said:**
> [http://forum.aircrack-ng.org](http://forum.aircrack-ng.org)

Thank you for the reply. I believe I got it to work from the link I posted in my previous one. I just needed to change two things around.

---

