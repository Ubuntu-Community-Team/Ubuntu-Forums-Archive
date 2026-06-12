---
title: "Please help with wireless!! Please"
date: 2009-09-16
forum: General Help
---

### Post by xdweaver on 2009-09-16
Okay so good morning to you all. So I have been working tring to get my wireless card to work. I have a Dell Inspiron 1300. I was getting help from a feller who was a great help to me and he got the wireless network light to come on the laptop. But it still will not connect. I have to be honest, I just don't have a clue on what to do. I am hoping that one of you will. So the other guy wanted me to type this in and post the results so here is where I am:
 

 lspci -nn :00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02
----------------------------------------------------------------------------------------------------------------------------
 

  [B]lshw -C network: arlene@arlene-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network:0 
description: Ethernet interface
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 02
serial: 00:14:22:ae:a5:af
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.3 latency=64 module=ssb multicast=yes
*-network:1
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 3
bus info: pci@0000:02:03.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network:0
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:14:a5:92:84:62
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 1a:42:21:bf:5f:bd
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/B]
 

  **ifconfig -a.: **arlene@arlene-laptop:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:14:22:ae:a5:af 
inet addr:192.168.0.3 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::214:22ff:feae:a5af/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:4874 errors:0 dropped:0 overruns:0 frame:0
TX packets:3869 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:4025266 (4.0 MB) TX bytes:777739 (777.7 KB)
Interrupt:18 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:112 errors:0 dropped:0 overruns:0 frame:0
TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:8528 (8.5 KB) TX bytes:8528 (8.5 KB)

pan0 Link encap:Ethernet HWaddr 1a:42:21:bf:5f:bd 
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wlan0 Link encap:Ethernet HWaddr 00:14:a5:92:84:62 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wmaster0 Link encap:UNSPEC HWaddr 00-14-A5-92-84-62-00-00-00-00-00-00-00-00-00-00 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 

 **I hope someone out there can help.. thanks for any help.. :)**

---

### Post by danwood76 on 2009-09-16
What have you done so far?

With the broadcom wifi cards you need the firmware to load into the card.

To do this automagically you can run this command to install the cutter:
```

sudo apt-get install bcm43xx-fwcutter

```
Then reload the bcm module with:
```

sudo modprobe -r bcm43xx && sudo modprobe bcm43xx

```

Once this last command is dont can you post the output of:
```

dmesg | tail

```

---

### Post by VastOne on 2009-09-16
Check this thread out. It has been a while since I worked on it, but you may find info there to help you out.


[http://ubuntuforums.org/showthread.php?t=517494](http://ubuntuforums.org/showthread.php?t=517494)

---

### Post by danwood76 on 2009-09-16
Scratch that, a quick google reveals that this card is probably not supported and you may have to use ndiswrapper and the windows drivers.

Check this link:
[http://florisla.be/blog/archive/2008/10/bcm4318-ubuntu/](http://florisla.be/blog/archive/2008/10/bcm4318-ubuntu/)

---

### Post by StuartN on 2009-09-16
> **xdweaver said:**
> **I hope someone out there can help.. thanks for any help.. :)**

What version of Ubuntu are you using? The support for my Dell 1501 with Broadcomm BCM4311 has improved with every release, to the point it works out of the box now.

---

### Post by xdweaver on 2009-09-16
jaunty 9.04. gotta ask this, and slap me me if i am being a dumb noobi, but is there i config my wireless by pluging into the ethernet? that is how i am online right now, just the wireless is fubar. lol DAMN I LOVE COMPUTERS  LOL

---

