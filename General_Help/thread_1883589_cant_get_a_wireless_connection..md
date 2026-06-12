---
title: "cant get a wireless connection."
date: 2011-11-19
forum: General Help
---

### Post by Agent26 on 2011-11-19
hi there all, 
I have installed xubunto 10.4 within windows but i'm unable to connect to the web useuing wireless. Can somebody help me please.
Thankyou

---

### Post by Agent26 on 2011-11-19
Hi there all, I hope I didn't upset any linux people by late replys and not marking things solved, i'm a forum noob too and have marked everything I posted now with thanks.
Sorry people.
 
So now i'm a bit more familuar with linux and set up with an install on my desktop of xubuntu 10.4.2 and a install on my lappy but inside windows and that's 10.4.2 aswell.
 
 
 
What might be the best program from the software center to set me up.
 
I can get into my router settings ect so just a quick reply to send me in the right direction would be brilliant.

---

### Post by linuxrev on 2011-11-28
Ancient wisdom: the surest way to get a wireless working is to wire it. I've gone through spells of working & not working wireless and am currently in the positive spell again. Nevertheless, I normally just wire it, using [Devolo powerline adapters]("http://www.devolo.com/consumer/dlan-mains-supply-network-via-powerline.html?l=en").

---

### Post by Agent26 on 2011-11-29
Thankyou so much linuxrev, I'm on it....
p.s If  can just get wireless up and running then I feel confident enough to say byebye to windows of my lappy altogether.
 
My desktop is now transformed, it has the wire so I got the web and all is perfect, I actually have a new 1.8 processor on the way and ive just grabed another gig and a half ram too and thats already in. A fast good system, quite a tranformation from millenium edition with 256mb and a 0.8ghz processor!
 
Just this laptop wireless prob and thats it.

---

### Post by gandaran on 2011-11-29
> **Agent26 said:**
> Thankyou so much linuxrev, I'm on it....
p.s If  can just get wireless up and running then I feel confident enough to say byebye to windows of my lappy altogether.
 
My desktop is now transformed, it has the wire so I got the web and all is perfect, I actually have a new 1.8 processor on the way and ive just grabed another gig and a half ram too and thats already in. A fast good system, quite a tranformation from millenium edition with 256mb and a 0.8ghz processor!
 
Just this laptop wireless prob and thats it.
hi
the number one wireless problem is drivers! this is the first one you have to check out, does the laptop wireless card work with the built in kernel drivers or do you have to install them?
find out the wireless chipset brand using these commands and post the output here
for internal devices
```
lspci
```
usb devices
```
lsusb
``` 
and also the full output of this
```
sudo lshw -C network
```
we will check if and what you need to install

---

### Post by Agent26 on 2011-12-03
Hi there Gandaran, sorry about the late reply.

OK I will attempt to get the information for you. But from what I can tell Xubuntu reconises  the card and it just needs to be enabled.

Still here is the info on the chipset...

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

and here is the usb devices...
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 13fe:1f00 Kingston Technology Company Inc. DataTraveler 2.0 4GB Flash Drive / Patriot Xporter 32GB (PEF32GUSB) Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and finally.....
*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:5d:ff:3d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.0.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:1a:04:30:a6:e7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
dave@ubuntu:~$ 

Thanks for the help, I am very greatfull.

---

### Post by gandaran on 2011-12-05
> 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
if you have wired internet check in additional drivers to activate the broadcom wireless driver
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access)

---

### Post by Agent26 on 2011-12-06
Hi Gandaran,
Thankyou I followed the instructions on that page installed the correct drivers, updated and enabled using terminal and now i'm online with my wireless, I though i'd never get it going.

You rock and are the Linux guru!!!!!
Thankyou.
Problem solved!!

---

### Post by westdale on 2011-12-06
Hi 
I am struggling in a simiar way
My Compaq CQ62 reports that it has Realtek ethernet and wireless(driver rtl1819xse)
Do you have a link to information on getting drivers for that ?

many thanks

---

### Post by westdale on 2011-12-06
Now upgraded to 10.10 and that has fixed the wireless connection
(also fixed an issue with speakers not working ) 

:-)

---

### Post by bluexrider on 2011-12-06
> **westdale said:**
> Now upgraded to 10.10 and that has fixed the wireless connection
(also fixed an issue with speakers not working ) 

:-)

I think I would have done that in the first place. Good

If you decide to go beyond that I think a live CD would be a good idea to make sure everything works before installing. imho

---

### Post by westdale on 2011-12-06
I wanted to stick with LTS version ... but needs must ...

---

