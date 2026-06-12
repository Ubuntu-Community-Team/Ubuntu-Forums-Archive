---
title: "Network problem"
date: 2011-05-20
forum: General Help
---

### Post by fmazon3 on 2011-05-20
I have a problem with my network. It says "network disconnected" even though the enable networking is ticked. Ive no idea what the problem is, it was static ip before, and i think i added another laptop, and it somehow stole my htpc's internal ip address, and it stopped working since then. any help would be greately appreciated. Btw only this htpc with ubuntu wont work with the internet, my windows pc's all have internet.


my /etc/network/interfaces has 
auto lo
iface lo inet loopback


When i did ifconfig I got
```
eth0      Link encap:Ethernet  HWaddr 00:30:67:9e:84:9f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:30:67:9e:84:9f  
          inet addr:169.254.9.4  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:41 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102980 (102.9 KB)  TX bytes:102980 (102.9 KB)
```
and when I did lspci I got

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4250]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

```


Should I just reset my router and see?

---

### Post by linuxinstalledfromhdd on 2011-05-20
You are probably having IP collision.

---

### Post by fmazon3 on 2011-05-21
well, I reset my modem and still having problems. I tried connecting directly from the modem to ubuntu machine, nothing.
So i removed the network-manager and only configured the file in /etc/network/interfaces

then I did sudo ifup eth0. 

its still not working and I'm also getting "no working leases in persistent database - sleeping" error

---

### Post by linuxinstalledfromhdd on 2011-05-21
ip collision.

---

### Post by 5149.5 on 2011-05-21
> **linuxinstalledfromhdd said:**
> ip collision.

There is no collision. The eth0 interface does not have a proper address.

---

### Post by linuxinstalledfromhdd on 2011-05-21
then the user would need to enable their mac address to be allowed from the router itself proabably.  This is probably a router issue.

---

### Post by 5149.5 on 2011-05-21
> **linuxinstalledfromhdd said:**
> then the user would need to enable their mac address to be allowed from the router itself proabably.  This is probably a router issue.

Nope. Are you just guessing?

The /etc/network/interfaces file needs to be changed for dhcp. Try adding this line to the file:

```
iface eth0 inet dhcp
```

---

### Post by linuxinstalledfromhdd on 2011-05-21
if the user doesn't know how their router is configured, it could be an office environment and someone walked in with a laptop and wants access to it.  We all are guessing here. ;)

---

### Post by 5149.5 on 2011-05-21
> **linuxinstalledfromhdd said:**
> We all are guessing here. ;)

Some more than others. :P The clue is the 169.254 address on eth0. That is referred to as a link-local address. Look it up.

---

### Post by linuxinstalledfromhdd on 2011-05-21
I'm going to research it. Interesting. ):P

---

### Post by fmazon3 on 2011-05-21
waaawww a clean install didnt fix the problem. WTF i lost all my xbmc settings too!


I already reset my router and modem. Changed the dhcp on, on the router as well. 

Well its a home network, and just adding one more lappy shouldn't do anything. 

Maybe the Interrupt:41 has to do something?

I'll try using my wifi adapter and see.


EDIT: ok so WIFI works apparently. WTHH. SHouldve tried this before reinstalling the whole os. Well anyhow, I tried switching ethernet cables for wired access, no luck. I mean, the network driver couldnt possibly just stop working randomly from the motherboard.


also here is the ifconfig output again. Does the interrupt:41 has to do anything?

```
eth0      Link encap:Ethernet  HWaddr 00:30:67:9e:84:9f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94928 (94.9 KB)  TX bytes:94928 (94.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:b2:33:56:d0  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:b2ff:fe33:56d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:95 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49154 (49.1 KB)  TX bytes:19075 (19.0 KB)


```

---

### Post by 5149.5 on 2011-05-21
You didn't have DHCP enabled on your wired connection before the reinstall. You should have tried my fix before reinstalling. Do you have DHCP enabled on eth0 now?

---

### Post by fmazon3 on 2011-05-21
> You didn't have DHCP enabled on your wired connection before the reinstall. You should have tried my fix before reinstalling. Do you have DHCP enabled on eth0 now?no no I had that fix you gave me too, I had it added, plus tried other things too.

and now as well, I added 
iface eth0 inet dhcp
no luck.
i tried connecting my windows laptop wired, and it works. As of now, it does seem like the hardware problem..

---

### Post by 5149.5 on 2011-05-21
Do you get any errors when you enter:

```
sudo /etc/init.d/networking restart
```

---

### Post by fmazon3 on 2011-05-21
it shows no problems when i restart my network like that.


btw, what were you saying about link local ip addresses.. I'm getting this ip again 169.254 address on eth0
EDIT: i tried it again and this is what i got

```
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:30:67:9e:84:9f
Sending on   LPF/eth0/00:30:67:9e:84:9f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

```

---

