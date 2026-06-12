---
title: "Internet Problem"
date: 2009-10-30
forum: General Help
---

### Post by Dark Sorrow on 2009-10-30
I am unable to access internet through ubuntu however i am able to do so through my windows. I can't access through Firefox or Opera(both of them are not working in off line mode). I am not able to update my system or download packages.
It gives error stating connect to internet(on the browser) however on the desktop environment connection established message appears.

---

### Post by Monotoko on 2009-10-30
How do you connect to the internet? Wifi? Mobile? Ethernet?

---

### Post by Dark Sorrow on 2009-10-30
> **Monotoko said:**
> How do you connect to the internet? Wifi? Mobile? Ethernet?
Ethernet and Mobile.
In both the above it gives the same error.

---

### Post by hal10000 on 2009-10-30
You should be  little more informative. What did you do to get it working? Did you already try to configure them with network-manager? What kind of devices do you have (usb, pci card or whatever) and who is the manufacturer of the devices? Where are the devices connected to (Accesspoint, hub, switch, router, modem or what else)?

Open a terminal window, perform the following commands and post their outputs here (you can mark the output with your mouse and paste it with the middle mouse button):

```

lspci
lsusb
ifconfig
iwconfig
route

```

---

### Post by purnateja on 2009-11-08
Hi,
even im facing the same issue.
I have both LAn and Wlan.
no internet though :mad:. and also no synaptic :mad:

im updating with all the info, pls have a look.

lspci:
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82G33/G31/P35/P31 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IH (ICH9DH) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7300 GT] (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1)
07:00.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
 
lsusb:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

iwconfig
wlan0     IEEE 802.11bg  ESSID:"WA1003A"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:50:F1:12:12:10   
          Bit Rate=36 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

route:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
default         WA1003A.Huawei  0.0.0.0         UG    0      0        0 wlan0

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:19:d1:9e:a6:69  
          inet6 addr: fe80::219:d1ff:fe9e:a669/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1163 (1.1 KB)  TX bytes:5988 (5.9 KB)
          Memory:92200000-92220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:9a:0a:f8:b5  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:fe0a:f8b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7951 (7.9 KB)  TX bytes:9160 (9.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-9A-0A-F8-B5-30-61-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by hal10000 on 2009-11-08
@purnateja:

> wlan0 Link encap:Ethernet HWaddr 00:17:9a:0a:f8:b5
inet addr:192.168.1.4 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::217:9aff:fe0a:f8b5/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:30 errors:0 dropped:0 overruns:0 frame:0
TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:7951 (7.9 KB) TX bytes:9160 (9.1 KB)

It seems as if your wireless card has a connection. The second line shows, that you have an ip-address (192.168.1.4)

Are you connected via a router and is this address configured by dhcp or did you configure it using a static ip?

Maybe you have nameserver problem. Look into the file [COLOR="Red"]/etc/resolv.conf[/COLOR] and see if there's a line similar to this one:
```
nameserver 192.168.1.1
```
If you don't have such a line or if the file is empty, then you have to fill in the address of your nameserver. This might be either the address of your router (presumably 192.168.1.1) or the ip-address of your provider's nameserver (or both)

---

### Post by Dark Sorrow on 2009-11-09
> **hal10000 said:**
> You should be  little more informative. What did you do to get it working? Did you already try to configure them with network-manager? What kind of devices do you have (usb, pci card or whatever) and who is the manufacturer of the devices? Where are the devices connected to (Accesspoint, hub, switch, router, modem or what else)?

Open a terminal window, perform the following commands and post their outputs here (you can mark the output with your mouse and paste it with the middle mouse button):

```

lspci
lsusb
ifconfig
iwconfig
route

```

This is the output i received when i executed those commands.

---

### Post by Dark Sorrow on 2009-11-09
> **hal10000 said:**
> @purnateja:



It seems as if your wireless card has a connection. The second line shows, that you have an ip-address (192.168.1.4)

Are you connected via a router and is this address configured by dhcp or did you configure it using a static ip?

Maybe you have nameserver problem. Look into the file [COLOR="Red"]/etc/resolv.conf[/COLOR] and see if there's a line similar to this one:
```
nameserver 192.168.1.1
```
If you don't have such a line or if the file is empty, then you have to fill in the address of your nameserver. This might be either the address of your router (presumably 192.168.1.1) or the ip-address of your provider's nameserver (or both)

My [COLOR="Red"]/etc/resolv.conf[/COLOR] a line similar to this one:
```
# Auto Generated
nameserver 192.168.1.1
```. As far as i remember the problem started after i tried to create/establish a wireless network connection(through my mobile), after that i could not connect to internet through wireless connection nor from fixed wired connection.

---

### Post by hal10000 on 2009-11-09
I suppose your wireless network card is plugged in via CardBus (PCMCIA), is that right?
It seems as if this card is not recognized correctly by ubuntu, which can be due to several reasons:

1.) The card is incompatible with linux (then you are out of luck)
2.) A missing driver
3.) missing software (e.g. pcmcia-tools)

As kong as you don't tell something more about your card (manufacturer, model etc.) and the way you want to connect it (Accesspoint, wireless router, static or dynamic ip-address) i can't help you any further in this case.

I suggest you plug off the wireless card and try to establish a wired connection with your network-manager to see if you can at least get an internet connection that way.

Btw., if you want to get a better network configuration tool than the crappy network-manager, try out wicd.

---

