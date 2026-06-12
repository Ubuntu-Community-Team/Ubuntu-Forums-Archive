---
title: "need help"
date: 2010-12-29
forum: General Help
---

### Post by teklife on 2010-12-29
Hi all. I am on my at least 5th reinstall of pinguy os. Several times in the past, i've had to do a reinstall because of some problem I couldn't figure out, but my current system is so customized that I would hate to have to do it yet again. Maybe someone here can help, and in the process i'll learn a little more myself. 

I have googled extensively about the following problems, and while I couldn't resolve the issues i'm having, I will post the info and error messages which I think are relevant to each particular problem, and hopefully that will help the more knowledgeable among us to troubleshoot more effectively. I will try to be as succinct as possible. 

**1) flaky wifi**. My wireless connection drops consistently. It's guaranteed it will happen, it's just a matter of time. I have my own home network, an airport express (b,g,n) with wpa-wpa2, but I have a much better connection on a neighbor's open 'linksys' network, although connection drops on both eventually.

When I do lose the connection, the first thing I try to do is reconnect via the list of networks on the wireless menu.  Sometimes it works, but usually I have to try several times. Sometimes I have to disable, then re-enable networking several times before i'm able to connect again. 

When that doesn't work, I have to reboot. If i'm lucky, wifi will work again after the first reboot, but usually, I must reboot several times; sometimes I have found it effective to kill the power in the beginning of the reboot a few times, before it gets to the point where you have to hold the power button down for a while to kill it.

This computer is a dual boot dell mini 10v with mac os x 10.6 being the other os. When the wifi gets funky and I have to reboot, sometimes it will just auto boot to the mac side (the default), where it sometimes still doesn't work(until I do several reboots). Isn't that weird? How can something on the linux side be affecting how the hardware works on the mac side? However, if I boot straight into the mac side, and the wireless is working fine right away, it will continue to work with no problems. The wifi gives me trouble, only  on the linux side.
	
	here's part of the error message I get in the log file viewer. “ **b43-phy0 ERROR: MAC 	suspend failed**” and “**[UFW BLOCK] IN=wlan0 OUT= MAC**”
	And here's some info from the terminal which may be helpful.
	
**	$ lspci -nn**

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02) 

**	lsusb**

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 045e:0059 Microsoft Corp. Wireless IntelliMouse Explorer
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 002: ID 0c45:63e3 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**	lshw -C Network**

WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:26:b9:9d:65:9d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:43 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 70:1a:04:a0:c8:f3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-24-generic firmware=N/A ip=192.168.1.107 multicast=yes wireless=IEEE 802.11bg

**	 uname -rm**

2.6.35-24-generic i686


**	iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:6C:F7:58   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**2) Can't mount my iphone**. It used to work fine, but now when I connect it, I get the following error that pops up:

[b]Unable to mount “tricorder” 
DBus error org.freedesktop.DBus.Error[/b].NoReply: Message did not receive a reply (timeout by message bus)
		
	By googline for that error message, and reading various forums, it seems possible that this may 	be due to the ios 4.2 update, which my phone has been updated to, but I don't remember exactly 	when I started getting that error, as my previously jailbroken iphone is now in iphone limbo, and i'm not using it daily as a phone.		

**3) Cannot get two finger scroll/right click to work consistently.**
This is one problem I have spent countless hours trying to sort out. I googled and read dozens and dozens of pages, and followed instructions on how to get my synaptics trackpad working with 2 finger scroll. I was never able to get it working, and I had given up on it, until recently, when I found an invisible file in my users home folder called “.twofingers” just checked it, and there's no .sh extension, but i'm pretty sure it's a shell script as  it looks that way by the icon. When I double click and run that script, 2 finger scroll finally works! Woohoo! But after a while, it just stops working and I have to keep re-running the script. Actually, the 2finger scroll stops working, but the 2 finger right click stays working. I have to re-run the script to the scroll back. 

I have tried to add this script to the startup items several different ways, but i've not yet been able to get the functionality to work automatically on startup. What am I doing wrong? What's going on with this script behaving so erratically? Now that i've finally got it working thanks to the script, how do I get the 2finger scroll/click working permanently? Here's the text inside the script: 

#!/bin/bash
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48

**4) Cannot install Boxee**. Boxee is neat, and I would like to include it in my own remastered pinguy. I've tried to install it via package managers, and by downloading the software from their site, and I always get some error. The error message it get when I try to install it via the mint menu is “**Can not install 'boxee' (E:Unable to correct problems, you have held broken packages.)**” Ubuntu software center says “**Package dependencies cannot be resolved**. *This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time*” How do I find which are these so called broken packages and get boxee to install correctly?

I've recently become totally in love/obsessed with linux, and i'm doing my best to spread the word, and turn people on to it. I'm trying to take the best version of linux i've found to date (pinguy os) and add some extra stuff on that I know my friends and family will like/use, but I need to get this system working well before I can clone it and install it on other people's computers. I hope these are just simple problems after all. Thanks.

---

