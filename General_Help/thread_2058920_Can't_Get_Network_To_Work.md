---
title: "Can't Get Network To Work"
date: 2012-09-16
forum: General Help
---

### Post by jsharin on 2012-09-16
Hey, I can't get my wireless network to work. I don't really know what I am doing, but when I try to ping any website, there is an error (Destination Host Unreachable). I have messed around a bit with /etc/network/interfaces, and I can't fix it. Any help is appreciated.

I have Ubuntu Server 12.04 installed. I just installed it (today), adding a LAMP and SSH server from the CD. Other than my slight adjustments to the aforementioned file, I haven't changed anything, and yet it doesn't work.

EDIT: After many adjustments of my files, I eventually came upon a solution that would work for about 1s before closing, and giving this error message:
```
phy0 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
phy0 -> rt2x00lib_autowakeup: Error - device failed to wakeup.
```
After much searching and attempts I found that this fixes the problem:
```
iwconfig wlan0 power off
```

---

### Post by blackened on 2012-09-16
Has networking ever worked on this machine?

Please post the output of

```
sudo lshw -c network
```

and

```
ifconfig
```

---

### Post by jsharin on 2012-09-17
At one point, on an earlier version of ubuntu, networking did work. At an even earlier point (now we're talking several years), windows had networking. But I completely reinstalled the new version of ubuntu from a CD, starting completely fresh.

```

*-network
description: Wireless interface
physical id: 1
bus info: usb@1:2
logical name: wlan0
serial: 00:12:17:a3:37:4b
capabilities: ethernet physical wireless
configuration: broadcasting=yes driver=rt2500usb driverversion:3.2.0-29-generic-pae firmware=N/A ip=192.168.1.107 link=no multicast=yes wireless=IEEE 802.11bg

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:576 errors:0 dropped:0 overruns:0 frame:0
TX packets:576 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:50934 (50.9 KB)  TX bytes:50934 (50.9 KB)

wlan0
Link encap:Ethernet HWaddr 00:12:17:a3:37:4b
inet addr:192.168.1.107 Bcast:98.229.129.255 Mask:255.255.255.0
inet6 addr: fe80::212:17ff:fea3:364b/64 Scope:Link
UP BROADCAST MULTICAST RUNNING  MTU:1500  Metric:1
RX packets:70 errors:0 dropped:0 overruns:0 frame:0
TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:8338 (8.3 KB)  TX bytes:11612 (11.6 KB)


```

---

### Post by Iowan on 2012-09-17
```
wlan0
Link encap:Ethernet HWaddr 00:12:17:a3:37:4b
[COLOR="Blue"]inet addr:192.168.1.107 Bcast:98.229.129.255 Mask:255.255.255.0[/COLOR]
inet6 addr: fe80::212:17ff:fea3:364b/64 Scope:Link
UP BROADCAST MULTICAST RUNNING  MTU:1500  Metric:1
RX packets:70 errors:0 dropped:0 overruns:0 frame:0
TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:8338 (8.3 KB)  TX bytes:11612 (11.6 KB)
```
Something seems amiss... :-k
Is the machine set up as wireless client, or did you set the address?
Another piece of information would be **route -n**

---

### Post by AndyOpie150 on 2012-09-17
It might be better to move this discussion over to the Network and Wireless sub-forum. The experts over there should be able to solve the problem a lot quicker. They helped me when I was having problems with my wireless connection on a new install of Ubuntu 12.04.

---

### Post by jsharin on 2012-09-17
```

Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 wlan0

```
I used the autoconfig from installation, which couldn't find my dhcp, so I went through the manual setup, 50-50 I messed up then. Also, I have been through /etc/network/interfaces a little in an attempt to fix the problem, so that's messed up now probably.

EDIT:AndyOpie150 may be right, I thought this may be a basic issue, but maybe its a specific one. I also contacted my wireless people, but they said they don't support Ubuntu, and pretty much stopped there.

---

### Post by AndyOpie150 on 2012-09-18
chili555 is the man. He'll hook you up.

---

