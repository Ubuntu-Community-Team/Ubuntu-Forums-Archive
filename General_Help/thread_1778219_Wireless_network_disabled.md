---
title: "Wireless network disabled"
date: 2011-06-08
forum: General Help
---

### Post by 3bdoo on 2011-06-08
i just installed ubuntu 11.04 on my LG R580 laptop, now i have windows 7 and ubuntu running.
my problem is i cannot connect to wifi, it shows that my wireless network is disconnected and i don't know why, my wired connection is working fine.
i have never used linux before so im kinda lost, the only thing i was able to do successfully so far is enabling my user account to connect to wireless networks through Users and Groups.

Here's what shows up when i use sudo lshw -c network :

  *-network DISABLED      
       description: Wireless interface
       product: RTL8192E Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:e0:4c:00:00:01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:fc700000-fc703fff
  *-network
       description: Ethernet interface
       product: Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 11
       serial: 00:24:54:c8:b2:46
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.11 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:41 memory:fc800000-fc803fff ioport:5000(size=256) memory:fc400000-fc41ffff

---

### Post by wildmanne39 on 2011-06-09
> **3bdoo said:**
> i just installed ubuntu 11.04 on my LG R580 laptop, now i have windows 7 and ubuntu running.
my problem is i cannot connect to wifi, it shows that my wireless network is disconnected and i don't know why, my wired connection is working fine.
i have never used linux before so im kinda lost, the only thing i was able to do successfully so far is enabling my user account to connect to wireless networks through Users and Groups.

Here's what shows up when i use sudo lshw -c network :

  *-network DISABLED      
       description: Wireless interface
       product: RTL8192E Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:e0:4c:00:00:01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:fc700000-fc703fff
  *-network
       description: Ethernet interface
       product: Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 11
       serial: 00:24:54:c8:b2:46
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.11 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:41 memory:fc800000-fc803fff ioport:5000(size=256) memory:fc400000-fc41ffff
Hi, first check in additional drivers and see if there is a driver for your wireless card there. Second go to the top right of the screen click on the internet conection icon and see if wireless is enabled.
If you are still having problems post the results of these commands back here.
```
nm-tool
```
```
ifconfig
```After you type the command copy and paste it here by clicking new reply then above the window you click on # and put the information in between the 2 code boxes ```

```

---

### Post by 3bdoo on 2011-06-13
Thanks for replying!
i actually checked all these things but didn't work. i tried installing the windows drivers in the windows wireless drivers, but when i restarted it removed the wireless part was completely gone from the upper right part instead of showing disconnected.
now when i type "lshw -c network" i get this:
[INDENT]  *-network UNCLAIMED     
       description: Network controller
       product: RTL8192E Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:fc700000-fc703fff
  *-network
       description: Ethernet interface
       product: Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 11
       serial: 00:24:54:c8:b2:46
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.9 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:41 memory:fc800000-fc803fff ioport:5000(size=256) memory:fc400000-fc41ffff
[/INDENT]
result for the "nm-tool"
[INDENT]State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:24:54:C8:B2:46

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             24.222.0.94
    DNS:             24.222.0.95
[/INDENT]result for "ifconfig"

[INDENT]eth0      Link encap:Ethernet  HWaddr 00:24:54:c8:b2:46  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:54ff:fec8:b246/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3092709 (3.0 MB)  TX bytes:373960 (373.9 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1920 (1.9 KB)  TX bytes:1920 (1.9 KB)
[/INDENT]

---

### Post by wildmanne39 on 2011-06-13
Hi, I did a little searching I found the driver you need and the instructions.
[http://www.box.net/shared/v1bpr94j8k](http://www.box.net/shared/v1bpr94j8k)
[http://ubuntuforums.org/showthread.php?t=1239342&highlight=RTL8192E+Wireless&page=9](http://ubuntuforums.org/showthread.php?t=1239342&highlight=RTL8192E+Wireless&page=9) 
First one is the driver second link is the instructions,look at the instructions first.

---

