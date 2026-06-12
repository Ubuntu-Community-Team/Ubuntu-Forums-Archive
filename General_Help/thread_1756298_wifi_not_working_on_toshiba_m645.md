---
title: "wifi not working on toshiba m645"
date: 2011-05-12
forum: General Help
---

### Post by gititdone on 2011-05-12
Just bought this toshiba laptop m645-s4114 today @ bestbuy and I installed the ubuntu 11.04 successfully erasing the MS OS on it but later realized my wireless network doesn't work. I have tried and followed everything that was given on some linux ubuntu forums with no avail. Any suggestions pls..

---

### Post by ambdeep on 2011-05-12
have you tried running the hardware drivers application. it fetches all the required proprietary drivers for the system. you'll probably need a lan connection while running this till your drivers a re installed.
you can also reinstall the system and while doing that run the same application while trying ubuntu, install the driver then install ubuntu if you dont have a lan connection around you.

---

### Post by gititdone on 2011-05-12
running the hardware application? Is it the-applications-additional drivers? i'm sorry about that i don't know how to go to that hardware drivers application.

---

### Post by ambdeep on 2011-05-12
yes...thats the one...sorry about the mixup..

---

### Post by gititdone on 2011-05-12
it's okay.yes i ran it and it say  -"no proprietary drivers are in use on this system". as in, nothing on it. right now i'm using cable to connect to the internet.

---

### Post by ambdeep on 2011-05-12
try :[http://ubuntuforums.org/showthread.php?t=885847]("http://ubuntuforums.org/showthread.php?t=885847")

---

### Post by gandaran on 2011-05-12
> **gititdone said:**
> it's okay.yes i ran it and it say  -"no proprietary drivers are in use on this system". as in, nothing on it. right now i'm using cable to connect to the internet.
did you update the software package list before looking in additional drivers?
```
sudo apt-get update
```
if still no drivers there after update then before you try anything post the output of these two commands so we can check what brand and model of wireless card.
```
lspci
```
and
```
lsusb
```

---

### Post by gititdone on 2011-05-12
@gandaran

lspci- the output is

cynthia-Satellite-M645:~$ lspci
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
06:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 5f)
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
cynthia-Satellite-M645:~$ 


lsusb-output is

cynthia-Satellite-M645:~$ lsusb
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
cynthia-Satellite-M645:~$

---

### Post by gititdone on 2011-05-12
@ ambdeep thanks i'll try this one and will let you know

---

### Post by gititdone on 2011-05-12
@ gandaran 

i also did the update in the software package list i just can't remember if i did it before looking for additional drivers, but i did the update.

---

### Post by gandaran on 2011-05-12
> 06:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 5f)
due to being open source intel drivers are included in the kernel already so you wont see any in additional drivers, normally intel wireless cards work out of the box on Linux OS, try the ndiswrapper guide, I hope you get it fixed, sorry I wasn't of any help.

---

### Post by gititdone on 2011-05-13
@ gandaran thank you so much for your help we were actually at the right tract when you asked me to run some commands but we stopped at some point chili555 at the other threads i posted he managed to go at some lengths and we were able to hit and solved it. hope other people who had same problems will see that solved discussions on the other threads, thanks again. people like you makes a better world.

---

