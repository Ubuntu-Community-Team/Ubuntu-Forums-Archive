---
title: "What happened to my Ubuntu Internet Connection?"
date: 2011-05-26
forum: General Help
---

### Post by 2048Megabytes on 2011-05-26
First off here are my system specifications:

Processor: AMD Phenom II 945 Quad-Core (3.0 gigahertz)
Motherboard: GIGABYTE GA-M78SM-S2H SOCKET AM2+  
Video card: Asus ATI Radeon HD4670 
Random Access Memory: 2 gigabytes of PC2-6400 Super Talent 
Hard Drives: 320 gigabyte Samsung F4 Model HD322GJ/U and 80 gigabyte Western Digital WD800JB-00ETA0
Power Supply: OCZ StealthXStream OCZ600SXS 600 Watt
Operating System: Linux Ubuntu 10.04 32-bit and Windows XP Home Edition 32-bit

Ubuntu 10.04 is installed on the Western Digital hard drive, my Windows is installed on the Samsung F4 drive.  Okay, now on to my problem.

I made no changes to the Ubuntu operating system that I know of.  I have diagnosed that this is a software issue.  My Windows XP operating system connects to the Internet with no issues.  Using my System Monitor it shows there is absolutely no Internet connection in Ubuntu.  

I have tried rebooting several times and it did nothing.  Tried Firefox and Opera and both say there is no Internet connection.  

Also tried recovery mode for Ubuntu and that did not do anything either.

I know I could fix this issue re-installing Ubuntu but that is a long painful road I just do not want to travel presently.  Any suggestions?  I have run into a wall and want my Internet back for Ubuntu.

---

### Post by nemilar on 2011-05-26
Hi,

Are you using a wired or wireless connect?

Can you open a terminal, run the following commands, and post the output?

```
ifconfig -a 
```

```
lspci
```

```
lsusb
```

---

### Post by 2048Megabytes on 2011-05-27
I am using a wired connection.  I will open my Terminal and do as you asked and post the results.

---

### Post by 2048Megabytes on 2011-05-27
phenom-user@Phenom-Computer:~$ **ifconfig -a**

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:5a:2b:a8  

          BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:22 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:96 errors:0 dropped:0 overruns:0 frame:0

          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:11398 (11.3 KB)  TX bytes:11398 (11.3 KB)



phenom-user@Phenom-Computer:~$ **lspci**

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)

00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)

00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)

00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)

00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)

00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)

00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)

00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)

00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)

00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)

00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)

00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)

00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)

00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)

00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control

02:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]

02:00.1 Audio device: ATI Technologies Inc RV710/730

phenom-user@Phenom-Computer:~$ **lsusb**

Bus 004 Device 002: ID 046d:c31c Logitech, Inc. 

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 001 Device 003: ID 03f0:7311 Hewlett-Packard 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by nemilar on 2011-05-27
Ok, that's a good start.  It has eth0, so it's not a driver problem.  But eth0 doesn't have an IP address assigned to it.

Are you using DHCP or a static IP address?

---

### Post by 2048Megabytes on 2011-05-27
Dynamic Host Configuration Protocol (DHCP) is what I am using.

---

### Post by 2048Megabytes on 2011-05-27
Please help anyone?

---

### Post by linuxinstalledfromhdd on 2011-05-27
It could be that your router needs to add your MAC address to receive a IP. Have you contacted hardware support for your make and model of router to check this out? Or do you have a network administrator you can contact about this issue for verification?

---

### Post by 2048Megabytes on 2011-05-27
Maybe I can try to reset my router with my Ubuntu connected.

I can provide a MAC address if it helps.  It is the following:

00-1F-D0-5A-2B-A8 

Is there any link someone can guide me to on how to reset the connection?

---

### Post by linuxinstalledfromhdd on 2011-05-27
What kind of router are you connected to? Let's start from the beginning.  :)  Who installed it? What kind of security does it have configured?  Is anyone else connected to this router?

---

### Post by 2048Megabytes on 2011-05-27
I have cable Internet that is wired through a wireless router.  My desktop is connected through the wireless router but I am not on wireless.  Understand?

It goes modem, wireless router then wired into the desktop.

Edit:  I hooked up this simple network.  Three other laptops are connected in to the Internet through the wireless router.

---

### Post by Swagman on 2011-05-27
If your ISP is BT internet then it's a known issue.

Read this thread

[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473)

Quick fix is on Page 13

Original fix is on  page 9

---

### Post by 2048Megabytes on 2011-05-27
I might also add that the Internet connection was running fine for months.  Then yesterday, it suddenly doesn't work anymore.

Edit: I will try the fixes you posted Swagman.

---

### Post by 2048Megabytes on 2011-05-27
I couldn't get anything working with the network fixes.  I got sick of it and wiped the entire partition with my Ubuntu 10.04 on it.  I wiped the partition with Zilla Data Nuker. Now I reinstalled Ubuntu 10.04 off my installation disk and the Internet is working again.  Problem solved.

---

