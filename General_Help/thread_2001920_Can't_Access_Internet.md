---
title: "Can't Access Internet"
date: 2012-06-11
forum: General Help
---

### Post by zinnakain on 2012-06-11
I am unable to access a wired internet connection from Linux. My friend set this computer up to dual boot windows xp and ubuntu  and I am posting from the windows partition.   I went to bed last night and it was working got up this morning and it was not.  I have no clue what happened in between.  The computer is an AMD Phenom II x4 955 running at 3.21g with 4g of ram and I am using 11.04 ubuntu (I think). I ran into a few suggestions such as kill process &quot;knetworkmanager&quot; (don't have it) and stopping the network manager service and restarting it.  I am not sure about that as if I remove the management service, which it says to do, how will I get it back if I can't access the internet from linux????? Any help will be appreciated as I will be stuck in windows until I can get the internet to work in linux.

---

### Post by HarryTorry on 2012-06-11
Could you paste the output of this command?
```
ifconfig
```

Unfortunately you'll have to boot into Ubuntu, paste it into a text editor (gedit for example) and then reboot into Windows. This has a strong chance of telling the problem!

---

### Post by zinnakain on 2012-06-11
eth0      Link encap:Ethernet  HWaddr              UP BROADCAST MULTICAST  MTU:1500  Metric:1           RX packets:0 errors:0 dropped:0 overruns:0 frame:0           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)           Interrupt:   eth1      Link encap:Ethernet  HWaddr              inet6 addr:  Scope:Link           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           RX packets:2 errors:0 dropped:0 overruns:0 frame:0           TX packets:30 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:1180 (1.1 KB)  TX bytes:5528 (5.5 KB)           Interrupt: Base address:   lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0           inet6 addr:  Scope:Host           UP LOOPBACK RUNNING  MTU:16436  Metric:1           RX packets:828 errors:0 dropped:0 overruns:0 frame:0           TX packets:828 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:64864 (64.8 KB)  TX bytes:64864 (64.8 KB) Sorry about the text, it will not display correctly for some reason

---

### Post by HarryTorry on 2012-06-12
Do you have two ethernet ports plugged in to your router?
You seem to be using IPv6 as well, are you sure that you are able to use it?

And does every localhost have a subnet of 255.0.0.0?
And shouldn't the localhost be on IPv6 if the network is?
(These questions aren't aimed at you, unless you know the answer, I'll make a thread soon if nobody replies)

---

### Post by zinnakain on 2012-06-12
yes, I have 2 internet access ports.  one is on the motherboard; but, that one the motherboard maker had problems with.  It would run for a few weeks then shut down or it would not run at all.  So, I bought a nic card and that is what I am running.  I removed the ip6 address and the hardware address as I thought that might be personally identifiable information.  As to the rest I have no clue, I assume I have the ability to use ip6 addresses.  it is enabled on the network manager icon in linux

---

### Post by HarryTorry on 2012-06-12
Well it would be helpful if you were to give the output again, but with the ip addresses and the subnet masks!
They won't be personally identifiable to you, since it's on a local network!

---

### Post by steeldriver on 2012-06-12
here are some  commands that will help us diagnose things (hardware / drivers / setup)

```
lspci | grep Ether
``` to show what ethernet controller(s) you have

```
lshw -C Network
``` more detailed info on network hardware and drivers

```
nm-tool
``` to show the current network-manager config

If you can grab this to a USB stick or save it somewhere you can read it from Windows and then post it back here - preferably surround it by CODE tags to make it easier to read (select the text and then press the # button in the message editor)

---

### Post by zinnakain on 2012-06-12
sorry about the length of time It took me to reply.  Here are the results (couldn't get the command lspci |grep ether to work, every time it would show nothing; but, I did get the command lspci to work; hopefully, it returned something that would be usefull to you)```
00):00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge 00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) 00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) 00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5) 00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40) 00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller 00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller 00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller 00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller 00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41) 00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40) 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40) 00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40) 00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) 00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller 00:15.0 PCI bridge: ATI Technologies Inc Device 43a0 00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller 00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller 00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration 00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map 00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller 00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control 00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control 01:00.0 VGA compatible controller: nVidia Corporation GF104 [GeForce GTX 460] (rev a1) 01:00.1 Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1) 02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03) 04:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 04:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) 05:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02) 05:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
```Here is the result os of the command ls hw -c network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 1c:6f:65:3d:22:d3
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:ce00(size=256) memory:fd9ff000-fd9fffff memory:fd9f8000-fd9fbfff memory:fd900000-fd91ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: eth1
       version: 10
       serial: 00:50:fc:f4:7d:30
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:21 ioport:be00(size=256) memory:fdeff000-fdeff0ff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```and here is the result of the command nm -tool
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        1C:6F:65:3D:22:D3

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             disconnected
  Default:           no
  HW Address:        00:50:FC:F4:7D:30

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on
[/CODE]
and here is the resubmitted info from the command ifconfig
```
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:3d:22:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 

eth1      Link encap:Ethernet  HWaddr 00:50:fc:f4:7d:30  
          inet6 addr: fe80::250:fcff:fef4:7d30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1180 (1.1 KB)  TX bytes:5528 (5.5 KB)
          Interrupt:21 Base address:0xbe00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64864 (64.8 KB)  TX bytes:64864 (64.8 KB)
```

---

### Post by steeldriver on 2012-06-13
Hi so it looks like you have 2 wired interfaces - I don't know anything about the RTL-8139/8139C/8139C+ but there are for sure issues reported for the RTL8111/r8169 card/driver combo. I don't know what the latest fix for that is - it may be as simple as unloading / blacklisting the driver or you may need to download and run an install script, e.g.

[http://ubuntuforums.org/showthread.php?t=2001224&highlight=RTL8111+r8169+r8168](http://ubuntuforums.org/showthread.php?t=2001224&highlight=RTL8111+r8169+r8168)

There are folks here (e.g. chili555) who would know for sure - but I  don't know what bat signal we need to send to have them stop by - meanwhile to be sure exactly what card we are dealing with can you please re-run the lspci command with the following options so that we pick up the PCI ID values:

```
lspci -nn | grep -i ether
```

(the '-i' makes it case-insensitive - I think the reason you didn't get anything before was 'Ethernet' versus 'ethernet')

---

### Post by zinnakain on 2012-06-13
yes, I have 2 ethernet controllers.  One is on the mobo (eth0), there is/was issues with that in both windows and linux so instead of waiting for the fix to arrive I went and bought a nic card (eth1) from a friend to get internet.
 He set this system up to dual boot both windows and linux so I can learn linux in anticipation of moving to linux.  But it looks like it might be best to continue to dual boot. Anyway enough of my life's story here are the results you wanted:

 result of lspci -nn | grep -i ether

```
 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03) 04:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
```

---

### Post by zinnakain on 2012-06-15
I did some further work into the problem

---

### Post by jmore9 on 2012-06-15
If you are not using the one on the motherboard then just go into the bios on the motherboard and disable it .  I disable everything i am not using such as onboard sound video serial ports , etc.

---

### Post by zinnakain on 2012-06-15
I removed et0 as I thought it could cause some weird behaviour such as switching drivers etc...no joy then I made sure I was pulling an ipv4 instead of an ipv6 address and viola I have internet.  thanks everyone

---

