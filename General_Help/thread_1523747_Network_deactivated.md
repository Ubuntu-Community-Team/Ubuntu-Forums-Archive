---
title: "Network deactivated"
date: 2010-07-04
forum: General Help
---

### Post by nachtbarjunge on 2010-07-04
Hi, 

I often switch the system to standby. Yesterday it did not resume any more so I reset the system. After rebooting the network was deactivated (written in the network manager in the Gnome tray). I did some more reboots, but it is still deactivated. 

The system:
CPU: Intel Core 2 Quad 
Mainboard: ASUS P5Q
LAN: PCIe Gigabit LAN controller featuring AI NET 2 (onboard, taken from the mainboard manual)
Ubuntu Lucid Lynx (amd64).  

When I open up "network diagnosis" from the menus, there is the loopback interface (lo) and eth0 listed. But there are no IPs listed for eth0. 
When I open up "network connections" from the menus there is no NIC listed.

This is /etc/network/interfaces:
```
auto lo
iface lo inet loopback

```

Are there any other configurations or log files that might help?

I am now running an Ubuntu 9.10 Live system and are able to write this :), so network is working. So I don't think it is a hardware issue \\:D/. 
In difference to the installed system the live system's:

[LIST]
[*] "network connections" lists "auto eth0"
[*]"network diagnosis lists IPs (distributed by DHCP)
[/LIST]
So seems DHCP is working, too. 

When I run "Systemtest" from the menu the NIC is recognized as "Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)". Seems to be different to the information from the mainboard manual. But its the same result on the installed system and the live system. 
I copied some paragraphs of the report (from the live system), where "eth" is written:
```
P: /devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth0
E: INTERFACE=eth0
E: IFINDEX=2
E: SUBSYSTEM=net

ethtool
6+20090307-1

libfreezethaw-perl
0.45-1

02:00.0 Ethernet controller [0200]: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller [1969:1026] (rev b0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8226]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 28
	Region 0: Memory at fe9c0000 (64-bit, non-prefetchable) [size=256K]
	Region 2: I/O ports at dc00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ATL1E
	Kernel modules: atl1e

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

```

I know there are similar issues described on the web, but most of them seemed to be OK after reboot. 

What should I do to get network reactivated? 

Thanks in advance.

---

### Post by clrg on 2010-07-04
What happens if you
```
sudo ifup eth0
```

or 

```
sudo ifup --force eth0
```

or 

```
sudo /etc/init.d/networking restart
```

or

```
sudo /etc/init.d/networking force-reload
```

or

```
sudo dhclient eth0
```

?

---

### Post by ajgreeny on 2010-07-04
Try something simple like ```
ifup
```in terminal.  I'm not sure if it needs **sudo**, so try both with and without if the first try does not work.

---

### Post by clrg on 2010-07-04
> **ajgreeny said:**
> not sure if it needs **sudo**

Changes to the network configuration require elevated privileges.

---

### Post by ajgreeny on 2010-07-04
Thanks, cirg.  I thought so, but have never needed to use *ifup* so was not certain.

I am now!

---

### Post by nachtbarjunge on 2010-07-04
Thanks. I'll reboot now and give it a try. I'll give a feedback after all.

---

### Post by nachtbarjunge on 2010-07-04
I tried all commands. Some give an output like this:
```
Ignoring unknown interface eth0=eth0
```

Its the last one that succeeds:
```
sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:22:15:63:86:93
Sending on   LPF/eth0/00:22:15:63:86:93
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.23 from 192.168.1.1
DHCPREQUEST of 192.168.1.23 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.23 from 192.168.1.1
bound to 192.168.1.23 -- renewal in 570255 seconds.
```

After this the LAN connection is up. But after rebooting I have to run it again. And the Gnome network manager still displays: "Network deactivated". I think it needs a restart.

[LIST]
[*]Why is eth0 unknown?
[*]Why does I have to run the DHCP query on every boot?
[*]What can I do to fix it?
[*]Seems like the system has some problems shutting down or booting, too. Sometimes the screen is black and I have to use the reset-button. May these problems be related?
[/LIST]

Thanks again.

---

### Post by clrg on 2010-07-04
I don't know why your interface isn't recognized on boot. Did you install an additional network driver which needs to be modprobed on every boot?

As a workaround, you could just ```
sudo bash -c 'echo "sleep 10; dhclient eth0 >/dev/null 2>&1" >>/etc/rc.local" '
```. 
Concerning your stability issues: There seems to be a serious issue with your machine. I've never seen a Linux machine crash (except when it was my fault ^^)

Do a 
```
sudo touch /forcefsck
```, that will run a fsck on your HDDs on the next reboot. Also, did you mess around with upstart/the init scripts? That might be the cause of boot/shutdown problems. 

For additional diagnostics, you could use [bootchart]("http://www.bootchart.org/") to monitor the boot process.

---

### Post by nachtbarjunge on 2010-07-04
There was a fsck running at boot time. Here is the content out of "boot.log":

```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 255687/1921360 files, 1829677/7679062 blocks (check after next mount)
/dev/sda5 has been mounted 27 times without being checked, check forced.
/dev/sda5: 61204/6881280 files (0.2% non-contiguous), 4032027/27519337 blocks
init: ureadahead-other main process (830) terminated with status 4

 * Starting AppArmor profiles       [80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

[74G[ OK ]
Not starting as we're not running in a vm.
 * Setting sensors limits       [80G 

```

I am not sure what it is going to tell me.

There is only the propriatary FGLRX-ATI graphics driver running. I installed it with the diver-tool from Ubuntu. 
I made some individual configurations for some applications. I can't remember all stuff that I did, but I am quite sure that I did not change any essential configurations especially nothing with the init process.

The system was running quite stable. The only problems a had with this system:

I had a second monitor which was hard to configure to a working 2-monitor-desktop. The monitor has a hardware-defect now. I think software caused hardware-defects happen pretty rarely, but I can't tell if this is the case here.

The other thing is, that I use Firefox really intense. There are many many tabs opened at the same time. Maybe this is the reason for some Firefox crashes that happened.

---

### Post by clrg on 2010-07-04
Yeah, Firefox tends to crash when you use 100+ tabs. I've seen it happening on other platforms as well.

---

### Post by nachtbarjunge on 2010-07-04
I can see that. But until now I would say, that just the Firefox process is hit by that and not other processes or even system stabilty.

---

### Post by noouch on 2010-07-13
Been having a similar problem here. Exact same symptoms, including

```
Ignoring unknown interface eth0=eth0
```
after I do
```
sudo ifup eth0
```

The difference is when I do

```
sudo dhclient eth0
```
I get:
```
sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:0b:6a:76:f9:6f
Sending on   LPF/eth0/00:0b:6a:76:f9:6f
Sending on   Socket/fallback
DHCPREQUEST of 0.0.0.0 on eth0 to 255.255.255.255 port 67
DHCPACK of 0.0.0.0 from 192.168.1.2
SIOCSIFNETMASK: Cannot assign requested address
SIOCSIFBRADDR: Cannot assign requested address
SIOCADDRT: No such process
bound to 0.0.0.0 -- renewal in 263572 seconds.
```

---

### Post by geralds on 2010-08-16
Just had the same issue for the same time. Wrote a short blog post that will hopefully help:
[http://my.opera.com/gsenarcl/blog/2010/08/16/k-x-ubuntu-network-manager-does-not-connect](http://my.opera.com/gsenarcl/blog/2010/08/16/k-x-ubuntu-network-manager-does-not-connect)

(in short: the issue for me was that one of the values in /var/lib/NetworkManager/NetworkManager.state got set to false during a crash; good luck!)

---

