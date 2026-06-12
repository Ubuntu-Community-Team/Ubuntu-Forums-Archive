---
title: "problem in wireless"
date: 2011-09-30
forum: General Help
---

### Post by yashar3600 on 2011-09-30
hello

i installed ubuntu 11.04
i can not connect internet via wireless. "enable wireless" is checked but the name of my wireless modem does not appear .
what should i do to resolve this problem?
thanks

---

### Post by An Sanct on 2011-09-30
Welcome to the forums!

Which wifi card/adapter are you using?

Can you connect the computer temporarily to the network with a cable?

---

### Post by yashar3600 on 2011-09-30
thanks
yes with cable i can connect to the internet .
but now i do not have access to the cable.


Which wifi card/adapter are you using?
i do not know.

---

### Post by An Sanct on 2011-09-30
Please paste the results of

```
ifconfig
```
and
```
sudo lshw -C network
```
(access the terminal via Alt+T *or* Alt+F2 & enter "konsole")
Please put them inside a "code" section (for easier reading), the ***'#'*** button above the forum input field.

The first command will show us how your network is configured and the second will '*ls*' list the '*hw*' hardware.

---

### Post by grahammechanical on 2011-09-30
When you can get a connection to the router by cable, go in the Dash and search for Additional Drivers and activate and drivers suggested. Or click the power icon and select System Settings and load the Additional Drivers utility from there. And a driver for your wireless adapter may be downloaded and installed. Then reboot and see if the name of your wireless modem is in the list.

Are other wireless networks in the list? If so, then you do not need a driver. Is your modem switched on? Are you in range?

Regards.

---

### Post by Abhinav Kumar on 2011-09-30
are u using a proxy ???
if yes enter the proper details and apply the settings.
change ur directory to /etc/apt and u will see a apt.conf file there . edit this file by sudo as 
Acquire  http:: proxy "http://username: password@ur_PROXY"
Acquire  http:: proxy "ftp://username: password@ur_PROXY"
Acquire  https:: proxy "https://username: password@ur_PROXY"
save this file and now check the wireless connection .

---

### Post by yashar3600 on 2011-10-01
thanks
i do not have access to cable for now.
i just install ubuntu and install opera browser(: and do not do any thing else.
there is no wireless modem name (wireless network) in the list.
i do not use proxy.

```
yashar@ubuntu:~$ sudo lshw -C network
[sudo] password for yashar: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f4500000-f4503fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 70:5a:b6:66:94:5c
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:48 memory:f4600000-f460ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:82:7b:1f:19
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
yashar@ubuntu:~$ 


```

and 

```
yashar@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 70:5a:b6:66:94:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5888 (5.8 KB)  TX bytes:5888 (5.8 KB)


```

---

### Post by gandaran on 2011-10-01
> description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
you will need to connect with wired internet to activate the broadcom wireless drivers in additional drivers or install from software center/synaptic

---

### Post by yashar3600 on 2011-10-01
is there any method such that i can download driver on windows and transfer it to ubuntu?

---

### Post by girlrepellent on 2011-10-01
I run a dual boot on my laptop with linux and windows and downloaded the drivers for my wireless card on my windows portion and dragged it to my home folder on my linux portion. Then did chmod +x [filename] and then ran it. You can probably do it with a USB drive and just transfer the drivers over in a similar fasion.

---

### Post by yashar3600 on 2011-10-01
but where  are drivers to download?

---

### Post by gandaran on 2011-10-01
> **yashar3600 said:**
> is there any method such that i can download driver on windows and transfer it to ubuntu?
yes, in fact there are many ways you can install the driver without internet connection, now that you know you need the Ubuntu Broadcom BCM4312 802.11b/g LP-PHY diver just google the subject on how to install without internet, you will find many ways to do it.

---

### Post by yashar3600 on 2011-10-01
i download drivers from this page
[http://packages.ubuntu.com/natty/bcmwl-kernel-source](http://packages.ubuntu.com/natty/bcmwl-kernel-source)
with installing all dependencies and bcmwl driver i can connect via wireless.
thanks to every body.
now i am going to migrate from windows to linux (:

---

### Post by Abhinav Kumar on 2011-10-01
:)

---

