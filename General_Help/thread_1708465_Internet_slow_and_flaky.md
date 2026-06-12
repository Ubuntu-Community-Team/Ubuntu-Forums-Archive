---
title: "Internet slow and flaky"
date: 2011-03-16
forum: General Help
---

### Post by linuxman94 on 2011-03-16
I have Ubuntu 10.10 installed on a computer with the specs listed below.  Occasionally my internet will stop working, forcing me to restart firefox.  Using ifdown and ifup fixes this, but it is annoying.  I have windoze vista installed and it does not have this problem.

EDIT: The computer is connected to a linksys WRT54G2 running stock firmware.

EDIT1: Here is the interfaces file:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.168.1.99
	netmask 255.255.255.0
	gateway 192.168.1.1
        network 192.168.1.1
	

```

Output of lspci | grep Ethernet
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
```

lshw:
```
description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 03
                serial: 6c:f0:49:d2:64:11
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.99 latency=0 multicast=yes
                resources: irq:42 ioport:ce00(size=256) memory:fddff000-fddfffff memory:fddf8000-fddfbfff memory:fdd00000-fdd1ffff

```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:d2:64:11  
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4906 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5194381 (5.1 MB)  TX bytes:694952 (694.9 KB)
          Interrupt:42 Base address:0xe000 

```

kernal version:
```
2.6.35-27-generic x86_64
```

---

### Post by TMcC on 2011-03-17
We've got several machines at work that use the RealTek RTL8111/8168B.

My advice would be to download the r8168 driver from: [ftp://WebUser:fH7s5YL@207.232.93.28/cn/nic/r8168-8.022.00.tar.bz2](ftp://WebUser:fH7s5YL@207.232.93.28/cn/nic/r8168-8.022.00.tar.bz2)

Which is a link found via: [http://www.realtek.com.tw/downloads/searchView.aspx?keyword=8168](http://www.realtek.com.tw/downloads/searchView.aspx?keyword=8168)

And then follow the instructions in the README file.

---

### Post by linuxman94 on 2011-03-17
Thanks, i'll try that and report back!

---

### Post by linuxman94 on 2011-03-17
So far it's good.  Will post back if i encounter problems.

EDIT: it's working well! thanks for the link!

---

