---
title: "No Internet connection after 10.10 Instal"
date: 2011-01-25
forum: General Help
---

### Post by Taswegian1 on 2011-01-25
Hi,
I successfully installed Ubuntu 10.10 on my second internal HD (36gb IDE) and now have a dual boot with Windows 2000. However I cannot connect to the Internet from Ubuntu and cannot see where to check any settings etc as I can in Windows Control Panel. My broadband ADSL modem is working ok in Windows. Can anyone help? Ubuntu isn't much good without an Internet connection!
 
Regards,
Ross Jones

---

### Post by mmsmc on 2011-01-25
is it wireless? if it is what wireless card do you have, go to the upper right hand corner of the screen do you see a cone shaped wireless bar with an exclamation mark on it? if it is pluggen to the internet what do you see?

---

### Post by Taswegian1 on 2011-01-25
Hi MMSMC,
   The internet connection is wired via a Sagem Fast 800 E3 ADSL modem.

---

### Post by TBABill on 2011-01-25
I think the question was more pointed toward your computer, not the connection. What type of device on your computer is being connected to your Internet service? Can you provide the output of ```
sudo lshw -C network
``` and ```
lspci
``` What I mean by "provide the output" is to go to Applications>>Accessories>>Terminal and just type in each code. Once you do the terminal will show a response. Paste the contents of that response back here so we can review and help you get it working. Each has to be done individually in the terminal. You'll need your password for the first command and it'll prompt you for it.
 
Does either wired or wireless work right now?

---

### Post by Taswegian1 on 2011-01-27
Hi TBABill,
 
The file outputs requested are as follows:
 
ross@ross-PC:~$ sudo lshw -C network 
*-network 
description: Ethernet interface 
product: 82545EM Gigabit Ethernet Controller (Copper) 
vendor: Intel Corporation 
physical id: e 
bus info: pci@0000:03:0e.0 
logical name: eth0 
version: 01 
serial: 00:0d:56:21:db:f9 
capacity: 1GB/s 
width: 64 bits 
clock: 66MHz 
capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k6-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair 
resources: irq:24 memory:fe7e0000-fe7fffff ioport:ecc0(size=64) 
ross@ross-PC:~$
ross@ross-PC:~$ lspci 
00:00.0 Host bridge: Intel Corporation E7505 Memory Controller Hub (rev 03) 
00:01.0 PCI bridge: Intel Corporation E7505/E7205 PCI-to-AGP Bridge (rev 03) 
00:02.0 PCI bridge: Intel Corporation E7505 Hub Interface B PCI-to-PCI Bridge (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81) 
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) 
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01) 
01:00.0 VGA compatible controller: nVidia Corporation NV18GL [Quadro NVS 280 SD] (rev a2) 
02:1c.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 04) 
02:1d.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 04) 
02:1e.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 04) 
02:1f.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 04) 
03:0e.0 Ethernet controller: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) (rev 01) 
04:0e.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 07) 
05:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) 
[EMAIL="ross@ross-PC:~$"]ross@ross-PC:~$[/EMAIL] 
 
The Internet connection is wired and is ok
 
Regards,
Ross

---

### Post by Taswegian1 on 2011-01-29
I belatedly read the Linux help on Internet connection (should have done this first). Right clicking on the Network icon and the Edit brings up an option to Add DSL which I did. A further dialogue box comes up with 3 data fields to be entered:
 
Username
System
Password
 
What do I put in these fields? My Linux user and Pasword? What is System?
 
Can anyone help please?

---

### Post by Taswegian1 on 2011-02-13
Is there anybody there????

---

