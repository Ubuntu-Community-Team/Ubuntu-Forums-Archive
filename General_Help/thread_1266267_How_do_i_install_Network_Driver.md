---
title: "How do i install Network Driver"
date: 2009-09-14
forum: General Help
---

### Post by Emdaer on 2009-09-14
Hi,

I recently got a new laptop, an ASUS U80V, and i want to make it run Ubuntu. My only problem is, that i have no network access, which means no internet.
I want to install the driver for:
Intel® Wireless WiFi Link 5100 ABGN
I found an .exe driver for this hardware, but how do i install it on my computer?

Regards
Emdaer

---

### Post by gordintoronto on 2009-09-14
> **Emdaer said:**
> Hi,

I recently got a new laptop, an ASUS U80V, and i want to make it run Ubuntu. My only problem is, that i have no network access, which means no internet.
I want to install the driver for:
Intel® Wireless WiFi Link 5100 ABGN
I found an .exe driver for this hardware, but how do i install it on my computer?

Regards
Emdaer

Linux handles drivers very, very differently from Windows.  I suggest you boot an Ubuntu Live CD, and see if the wireless adapter works.  What I have read elsewhere makes me believe it might.

When you run from the live CD, there will be a network manager icon near the top-right of the screen.  Right-click it, look for "edit connections."

---

### Post by P4man on 2009-09-14
> **Emdaer said:**
> Hi,

I recently got a new laptop, an ASUS U80V, and i want to make it run Ubuntu. My only problem is, that i have no network access, which means no internet.
I want to install the driver for:
Intel® Wireless WiFi Link 5100 ABGN
I found an .exe driver for this hardware, but how do i install it on my computer?

Regards
Emdaer

For most wireless card, you already have the drivers. That intel card is pretty new though, you got 2 options. First (which I recommend) is enabling ubuntu backports. That will make drivers for the upcoming ubuntu available to you. have a look here:

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

After enabling the ubuntu backports repository and doing an update, I believe your card will work fine.

If not, you can use windows drivers with a "hack". Its called ndiswrapper. You can enable it through add/remove programs (look for ndiswrapper and install it). Once installed, you can go to system > adminstration > ndiswrapper (or windows drivers or something) and make it load windows drivers (point it to the .inf file). 

Using ndiswrapper can cause some issues with standby/resume, and i strongly recommend trying the first approach first. More over, this ONLY works for wireless network cards. There are no other windows drivers you can use on linux, so don't try for printer or soundcard or something.

---

### Post by Emdaer on 2009-09-15
Can i enable Ubuntu Backports without internet access, using a CD or USB disk?
My laptop has no internet connection at all, no wired or wireless, since it has no driver for the Ethernet.

---

### Post by P4man on 2009-09-15
> **Emdaer said:**
> Can i enable Ubuntu Backports without internet access, using a CD or USB disk?
My laptop has no internet connection at all, no wired or wireless, since it has no driver for the Ethernet.

Neither wired nor wireless is working out of the box ?? Wow. Having just one of them not working is bad luck, I never heard any machine doing neither. Are you sure? What ethernet controller is in it, or what machine is it?

Anyway, if you're right, then Id suggest either borrowing a usb wifi stick that does work, or trying another distro that is less hostile to your machine.

---

### Post by P4man on 2009-09-15
ONe more thing.. someone else asked a similar question recently, only to find out his wifi was working just fine, he just didn't know how to use it.. so, click the network icon top right, and see if you don't have a list of wireless APs to connect to. Perhaps try switching the wifi radio off and on if you laptop has a key or button for it.

---

### Post by Emdaer on 2009-09-16
Well i suppose you're right, i have access to the wireless Internet. But i still thank you! If it wasn't for you i would still have this big problem. I'll try enabling backports and see if it makes my LAN work.
This is my first time posting at ubuntuforums and i really appreciate, that people help eachother, even if is a complete beginner as myself. You guys are you a great job. 
Thank You

Regards
The new happy ubuntu user
Emdaer

---

### Post by P4man on 2009-09-16
should have thought of it earlier :) People new to linux automatically assume its gotta be hard, and are so used to having to install drivers to get something working.. anyway, glad the wifi works.

For the ethernet, let's see what controller you have. Open a terminal (applications > accessories > terminal) and type

```
lspci
```
That will list all your onboard devices, copy paste the output here.

Do the same with

```
ifconfig
```

which will list all (working) network devices and their configuration.

---

### Post by Emdaer on 2009-09-16
lspci:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)

ifconfig:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3600 (3.6 KB)  TX bytes:3600 (3.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:23:07:88:4c  
          inet addr:10.1.3.117  Bcast:10.1.255.255  Mask:255.255.0.0
          inet6 addr: fe80::224:23ff:fe07:884c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75491 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:110039283 (110.0 MB)  TX bytes:4314154 (4.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-23-07-88-4C-38-34-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Commander_Keen on 2009-09-16
This may help you.
Go and buy a Netgear WG111V 2 or 3.  Its a USB wireless key that will work out of the box.

---

### Post by Daylon on 2009-09-16
> **Commander_Keen said:**
> This may help you.
Go and buy a Netgear WG111V 2 or 3.  Its a USB wireless key that will work out of the box.


my wg111v2 does NOT work out of the box lol...im having so much trouble finding a driver download for ndiswrapepr can you help me lol?

---

### Post by Commander_Keen on 2009-09-16
do a search on Threads that I started.
and there is a command to upgrade the wireless.

---

### Post by P4man on 2009-09-16
That wired network controller does indeed need a driver. Not seen that very often. Anyway, here is a how to:
[http://dtbaker.com.au/random-bits/ubuntu---ethernet-controller-attansic-technology-corp.-device-1063-rev-c0-.html](http://dtbaker.com.au/random-bits/ubuntu---ethernet-controller-attansic-technology-corp.-device-1063-rev-c0-.html)

---

### Post by Emdaer on 2009-09-17
The ethernet LAN works now. Many thanks.

---

