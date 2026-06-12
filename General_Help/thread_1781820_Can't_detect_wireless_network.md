---
title: "Can't detect wireless network"
date: 2011-06-14
forum: General Help
---

### Post by misterbreadcrum on 2011-06-14
I've just fully installed Ubuntu on my laptop.  I had it running as a secondary operating system and have switched over.  Now, however, I'm having all sorts of incredibly frustrating problems, one of which being that it won't detect the wireless networks around me!
Please, some one tell me how I can get the network manager to automatically detect wireless networks in range, this whole process has become very frustrating.

---

### Post by wildmanne39 on 2011-06-14
> **misterbreadcrum said:**
> I've just fully installed Ubuntu on my laptop.  I had it running as a secondary operating system and have switched over.  Now, however, I'm having all sorts of incredibly frustrating problems, one of which being that it won't detect the wireless networks around me!
Please, some one tell me how I can get the network manager to automatically detect wireless networks in range, this whole process has become very frustrating.
Hi, you have to install a driver for your wireless card. First look in additional drivers and see if there is one for your card if so install it. You have to be connected to the internet with a wired connection to check for the driver. If it is not there run this command in a terminal
```
sudo lshw -c network 
```
```
lspci
```and post the results back here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by misterbreadcrum on 2011-06-14
colin@colin-Satellite-M645:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
15:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
15:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
15:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
15:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
colin@colin-Satellite-M645:~$ sudo lshw -c network
PCI (sysfs)  

When I was only trying ubuntu as an operating system it picked up my 2wire network in literally a matter of seconds, why is this different?

---

### Post by TBABill on 2011-06-14
I think you may need to use a capital C in your lshw as ```
sudo lshw -C network
``` but you also may need to look at ```
lsusb
``` if this is a USB wireless device. I don't see it in your lspci.

---

### Post by misterbreadcrum on 2011-06-14
I did it with a capital C and it returned this
 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:46:7c:f5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.85 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:6000(size=256) memory:b0404000-b0404fff memory:b0400000-b0403fff
where do I get the driver or is this the information about the network I'm wired to?  I'm plugged into my network via an ethernet cable.

---

### Post by TBABill on 2011-06-14
We still need to see your lsusb output because it must be a plugin device.

---

### Post by misterbreadcrum on 2011-06-14
I found the driver on the internet and ran the .sh script in the terminal and was told to remove the old driver.  Does this mean there's already a driver installed?  I feel like this is a simple solution I'm just failing to see.

---

### Post by misterbreadcrum on 2011-06-14
Bus 002 Device 003: ID 0461:4d63 Primax Electronics, Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

this was my output after doing lsusb

---

### Post by misterbreadcrum on 2011-06-14
Any ideas anyone

---

### Post by wildmanne39 on 2011-06-14
Hi, go to this link and read the thread carefully and go to the other link when it tells you too, and you should get it working  have given this link to other people with the same card and they got theres to work.
Hi, sorry I removed the link, it was for the wrong connection, it appears you do not have a wireless card.

---

