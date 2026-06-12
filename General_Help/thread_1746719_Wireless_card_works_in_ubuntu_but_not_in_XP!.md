---
title: "Wireless card works in ubuntu but not in XP!"
date: 2011-05-02
forum: General Help
---

### Post by 666pluto on 2011-05-02
I know it's kind of strange asking for XP help in this specific forum, but bare with me and read the entire post :).

I own LG X120 notebook, and everything was working fine until i got rid of the default OS (XP) which came with it and made a full fresh install of XP! for some reason, while every hardware got installed properly, i couldn't install the W.CARD! I tried every driver out there, from realtek home page, MAIN LG site, Israel LG site, even got a few driver versions from LG technical support trough the mail...still, the system acts as the wireless card is unknown hardware- won't appear at all in network connections, no icon near the cloak, and in device manager it appear of course as "Unrecognized device- network controller". i tried to install every driver using the device manager directly, still not working, it keeps acting as i never installed it!

strange thing is, and that's after the LG support line already claimed it's 100% hardware problem, I installed ubuntu 10.10/11.04 and it automatically recognized and installed the wireless card! 

So, I'm guessing it's a drivers problem in windows xp, but how do i solve it? i was hoping, since the card works in ubuntu, someone could direct me to the right drivers for xp or any other technical stuff:).

in ubuntu, the wireless network card name is "RT3090 wireless 802.11n 1T/1R PCIe", in XP according to the notebook model "realtek 8187SE".

can anyone help me with this problem?

---

### Post by garvinrick4 on 2011-05-02
Darn Windows and their driver problems.!!! Never have drivers in the kernel like Linux.
Give this link a go.

[http://www.ehow.com/how_7414310_reset-wifi-card-lg-x120.html](http://www.ehow.com/how_7414310_reset-wifi-card-lg-x120.html)

---

### Post by 666pluto on 2011-05-02
Problem solved:D. the link didn't help much, it was the method i did as before. but i searched for "RT3090 wireless" driver this time, instead of realtek 8187SE, and now the wireless works!

it's a bit strange to me, why 8187SE's drivers are published in the manufacture's site for this notebook (same as was given to me by their technical support) while in reality RT3090 card is the one located inside the notebook? they could have saved me two weeks of headaches trying to solve this problem!

---

### Post by garvinrick4 on 2011-05-02
> it's a bit  strange to me, why 8187SE's drivers are published in the manufacture's  site for this notebook (same as was given to me by their technical  support) while in reality RT3090 card is the one located inside the  notebook? they could have saved me two weeks of headaches trying to  solve this problem!       I find if you always do a search for drivers first you cannot usually go wrong. I have a wifi card in one machine intel 1000 bgn and it will not work
with n enabled so have to disable n and it then shows as a intel 1000 bg in iwconfig and is stable at 58 Mb/s in g where in other operating systems works in n at 144 Mb/s big difference but at least it works because I spend 90% of time in Ubuntu. From what I understand intel is not going to fix that driver iwlagn. Just in case someone reads this Thread and has different info on iwlagn driver.
Here is how to locate cards and drivers network:  a little late but here it is:
```

 rick@rick-HP:~$ sudo lshw -C network
[sudo] password for rick: 
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:64:48:8f:52
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 ip=192.168.1.125 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:45 memory:d3500000-d3501fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:4d:62:62
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff
rick@rick-HP:~$ 

```

---

### Post by csh on 2011-05-04
It is because some version of your laptop model using another WiFi card.

---

