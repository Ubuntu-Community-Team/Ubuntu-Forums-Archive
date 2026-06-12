---
title: "Dell Precision M4400 Internet Connection Issues"
date: 2010-07-10
forum: General Help
---

### Post by wobert on 2010-07-10
Hello
 
I just finished installing the ubuntu 10.04 @64 bits on my dell precision M4400. I am encountering the issue that I can not connect to internet.
I thought that the wireless card was the only issue so then I tried plugging to the modem to try and get computer drivers through the administration hardware option but seems it can not connect.
 
Since I do not want to mess things, I would appreciate your help. I have another computer with access to internet, so I can download whatever you consider necessary for fixing my problem.
 
Computer has :
 
1 223-9143 MPWS M4400,P8400,(2.26GHZ),3M,CORE 2 DUO
1 310-8319 INTEL DUAL CORE 2,MEROM,NBK
1 310-9160 VISTA PREMIUM DOWNGRADE RLOB NOTEBOOK
1 311-8810 8.0GB DDR2-800MHZ,2 DIMM,MPWS
1 311-8818 FIPS CERTIFIED FINGRPRNT RDR,MPWS M4400
1 312-0729 6-CELL PRIMARY BATTERY,LAT E/MPWS
1 313-6459 8X DVD, MPWS
1 313-6471 NO WEB CAM W/MIC,WXGA LCD,MPWS M4400
1 313-6831 MICROPHONE ONLY,MPWS 4400
1 320-6719 NVIDIA QUADRO FX 770M,MPWS M4400
1 320-6720 15.4IN WIDE WXGA LCD,MPWS M4400
1 330-0832 RESOURCE DVD W/DIAG,DRIVERS,PWS M4400
1 330-0834 130W, 3P,AC ADAPTER,MPWS
1 330-0884 NO VPRO TECH ADV MGMNT FEATURES,LAT/MPWS
1 330-1525 US-6FT,3-PIN,FLAT POWER CORD, MPWS
1 341-6942 80GB HDD, 9.5MM, 5400RPM, MPWS MX400
1 420-9008 EMRP VBUS SP1 DGRD,XPPRO INSTALL,SP,MPWS
1 420-9184 CYBERLINK POWER DVD 8.1,MEDIA,LAT/MPWS
1 430-3084 DELL 1397 802.11B/G MC ROW,LAT E/MPWS, B
1 916-8097 HW WRTY + SVC,MWS4400,UNY,INIT LA
1 949-2040 BASIC NBD OS, MWS4400,UNY,INIT LA
1 916-8107 HW WRTY + SVC,MWS4400,EXT LA
 
I am really excited and hope to learn alot from ubuntu
 
thanks
 
 
 
This is the current status of my computer, I have tried moving the wireless switch several times and it continues to display the same staatus (DISABLED).
 
Hopefully someone can help me.
 
 
wobert@wobert-laptop:~$ sudo lshw -C network 
*-network 
description: Ethernet interface 
product: 82567LM Gigabit Network Connection 
vendor: Intel Corporation 
physical id: 19 
bus info: pci@0000:00:19.0 
logical name: eth0 
version: 03 
serial: 00:21:70:d0:38:5a 
capacity: 1GB/s 
width: 32 bits 
clock: 33MHz 
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.7-7 latency=0 link=no multicast=yes port=twisted pair 
resources: irq:29 memory:f6fe0000-f6ffffff memory:f6fdb000-f6fdbfff ioport:efe0(size=32) 
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
resources: irq:17 memory:f1ffc000-f1ffffff 
*-network DISABLED 
description: Wireless interface 
physical id: 2 
logical name: wlan0 
serial: 00:22:5f:5d:06:0f 
capabilities: ethernet physical wireless 
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
 
Information from my internet service provider:
 
Modem brand is 2wire gateway. 
For net ADSL.
Model: RG2701HG-00
 
The services is from infinitum (telmex) at Mexico
 
I do not dual boot with windows.
 
 
Did a ping to my modem, with the ethernet cable plugged and just with the inalambric card, having the same answer "network is unreachable"
 
 
 
Hope anyone can help me
 Anyone please help me

thanks

---

### Post by rm63 on 2010-11-22
Hi the problem is that the e1000e driver for intel ethernet card is not in the kernel (who knows why...).

Download (using you other computer) the driver e1000e-1.2.10.tgz (or later version) from the intel web site.

copy it into your would-be installed Ubuntu using a memory stick.

add the cdrom to /etc/apt/souce.list :
sudo apt-cdrom add
Sudo apt-get install build-essential linux-header-server linux-header-2.6.x.x-x 
(type uname -a to see your kernel version and replace the x's)
uncompress the driver's source code :
tar zxvf e1000e-1.2.10.tgz
cd e1000e-1.2.10/src
make
make install
modprobe e1000e
sudo ifconfig
now you should see your ethernet card ! :) 
Cheers,
Rémy

---

### Post by wobert on 2010-12-04
Thanks for your help.

I open another thread and this got solved.  

Please take a look of what was done, it might be the same thing you just mentioned

[http://ubuntuforums.org/showthread.php?t=1538035](http://ubuntuforums.org/showthread.php?t=1538035)

---

