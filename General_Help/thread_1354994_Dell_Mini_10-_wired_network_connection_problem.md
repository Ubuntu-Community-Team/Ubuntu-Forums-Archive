---
title: "Dell Mini 10- wired network connection problem"
date: 2009-12-14
forum: General Help
---

### Post by blur xc on 2009-12-14
So, I've got this Dell Mini 10 on which I've installed Karmic.  First off- besides the 800x600 resolution, is that the broadcom wifi didn't work.  I googled about, and found a fix that said to hook it up to a wired internet connection, and do a few sudo apt-gets to fix the problem.  I brought it to work, plugged it into our network- and BAM- nothing.  No internet.  

Any suggestions?

Thanks,
BM

---

### Post by shairozan on 2009-12-14
Hey, 

Just kind of a random thought, but have you tried just plugging it up at home? I know that here at work, I have port-security enabled on our switches so that only a single MAC can access the network. 

In order to see something else, can do you the following for me:

```
sudo ifconfig -a
```

and 
```

lspci
```

These will let me see if the eth0 / eth1 interface is registering and LSPCI will let us know if the system recognizes the interfaces.

---

### Post by blur xc on 2009-12-14
This is a Christmas gift for my wife, and I have four small kids at home w/ loose lips.  So, if I tried at home, I'd need ALL of them to be gone at the same time (almost never happens) or risk the kids seeing and accidentally saying something before Christmas.

I'll call our IT guy (it's small company, uh, just one employee, me) and ask if he set something like that up.  

Now- I've been googling this a bit, and I'm not hte only one with this problem, but almost all of them start out with run such and such command(s), and post output here.  Just one Q- how do you get the output from the pc w/o connectivity to a pc with connectivity?  Direct it to a text file, copy to flash drive, and go from there?  I can do that if I have to...

But- I did just run across this: [http://swiss.ubuntuforums.org/showpost.php?p=8090292&postcount=1](http://swiss.ubuntuforums.org/showpost.php?p=8090292&postcount=1)
which I got from this - [http://ubuntuforums.org/archive/index.php/t-1321463.html](http://ubuntuforums.org/archive/index.php/t-1321463.html)

I'll get back to you w/ the output from those commands.

thanks,
BM

---

### Post by blur xc on 2009-12-14
Ok- output from ifconfig -a:
```
eth3      Link encap:Ethernet  HWaddr 00:24:e8:cb:fd:24  
          inet6 addr: fe80::224:e8ff:fecb:fd24/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:510 (510.0 B)
          Interrupt:24 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```lshw -C network:
```
*-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: 00:24:e8:cb:fd:24
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:24 ioport:2000(size=256) memory:d8410000-d8410fff(prefetchable) memory:d8400000-d840ffff(prefetchable) memory:d8420000-d843ffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:d8000000-d8003fff

```lspci:
```
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```I don't have a live usb drive here with me, so I'm going to make one and try the fix from that other post.

Thanks,
BM

---

### Post by blur xc on 2009-12-14
yay!  I'm online!  I followed the instructions in this thread- [http://ubuntuforums.org/showthread.php?p=8090292#post8090292](http://ubuntuforums.org/showthread.php?p=8090292#post8090292)

It didn't let me directly install the broadcom driver right off the bat.  I had to install three dependencies (it told me what they were, and they were all on the live usb drive)...  

Now off to find my graphics fix!!

BM

---

