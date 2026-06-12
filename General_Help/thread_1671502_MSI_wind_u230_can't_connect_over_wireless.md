---
title: "MSI wind u230 can't connect over wireless"
date: 2011-01-20
forum: General Help
---

### Post by c@ssie on 2011-01-20
I've been trying to connect gt my wirelss running on my an MSI wind u230.
 
First I tried with the default  configuration; it could not find any wireless networks.
Then I tried the  [Ralink 3090 driver]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090") from Markus Heberling's PPA;  it still could not find any wireless networks. 
then I tridading  the followwing to  /etc/modprobe.d/blacklist.conf
<code>
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
</code>
and still could not find any wireless networks. 

Finally, I used the ndiswrapper with the windows driver.  I can now find the wireless networks but when I try to connect, I get a 'bad password" on encrypted wetworks and "cannot opbatain IP address" errors on unencrypted networks.

Anyone know how i can get wireless online?

---

### Post by c@ssie on 2011-01-20
I should also say that,  tested that the wireless worked, using windows, before i erased it to install ubuntu.  so At least i know the hardware works.

---

### Post by Big Dan on 2011-01-23
Hi Cassie, 

  I got a U230-086US two weeks ago and first thing I did was try Ubuntu on it. Booting from LiveUSB the wireless worked out of the box. Later on I wiped Windows 7 and installed Ubuntu the wireless worked before I installed the restricted drivers. 
   
   Can you look under the computer to see what specific model you have? There are more than a few submodels of the U230 though I doubt the wireless adaptor would be different between models.

-Dan

---

### Post by Lumsdoni on 2011-06-27
I had a similar problem.

Initially it was solved with the deb package from [https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)


Then a few days later it no longer connected.

Now I have the following situation.

Clean 64bit install of 10.04

Tried to reinstall the deb package, said it installed properly, rebooted, no wireless. Option to enable wireless is grayed out and network manager says Wireless is disabled.

sudo lshw -C network
```
 *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: ra0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.1.7 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 40:61:86:b3:13:dd
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.73 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:febe0000-febfffff(prefetchable)

```iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ]
```ifconfig

```

eth0      Link encap:Ethernet  HWaddr 40:61:86:b3:13:dd  
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:feb3:13dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2396231 (2.3 MB)  TX bytes:143561 (143.5 KB)
          Interrupt:28 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


```While I was experimenting with Ubuntu installs, NEWBIE, the deb package I used worked to enable wireless everytime, until this morning when it no longer worked.  I tried tons of stuff but decided a clean install followed by the reinstallation of the deb package would solve it as normal but to no avail.

Any ideas?

---

### Post by Lumsdoni on 2011-06-27
sudo ifconfig wlan0 up

```

wlan0: ERROR while getting interface flags: No such device


```

sudo ifconfig ra0 up

```

SIOCSIFFLAGS: Unknown error 132

```

---

### Post by Lumsdoni on 2011-06-28
I have solved this now.  Somehow Wireless got disabled, but hardware switch wasn't working.

I booted from a Live 11.04 CD, and hardware switch worked. 

Then rebooted in 10.04 and wireless was working again.

---

