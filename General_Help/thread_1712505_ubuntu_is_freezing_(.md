---
title: "ubuntu is freezing :("
date: 2011-03-22
forum: General Help
---

### Post by ufukeskici on 2011-03-22
After I login Ubuntu, 2-3 minutes later it is freezing.


 I don't know the reason. I've installed the lates Ubuntu updates but it still continues.


 Coul you please help me to find out the reason?

---

### Post by cookiecloud on 2011-03-22
> **ufukeskici said:**
> After I login Ubuntu, 2-3 minutes later it is freezing.


 I don't know the reason. I've installed the lates Ubuntu updates but it still continues.


 Coul you please help me to find out the reason?

Version? Architechture? Machine make/model/specs? etc...

These will assist us in diagnosing the probs.


CC :-)

---

### Post by ufukeskici on 2011-03-22
I'm using 64 bit OS with Ubuntu and Win7 at the same time.

I have asus main board and intel i7 processor

Ubuntu version is 10.04 LTS

---

### Post by cookiecloud on 2011-03-22
> **ufukeskici said:**
> I'm using 64 bit OS with Ubuntu and Win7 at the same time.

I have asus main board and intel i7 processor

Ubuntu version is 10.04 LTS

If you can get to a reasonably stable command prompt, type:

```

lspci

```

... and post the output here, or if you can take a (clear) photo of the output from that command and post it here, maybe we can helps ya :-)

Cheers!

---

### Post by s-p-n on 2011-03-22
> **ufukeskici said:**
> After I login Ubuntu, 2-3 minutes later it is freezing.


 I don't know the reason. I've installed the lates Ubuntu updates but it still continues.


 Coul you please help me to find out the reason?

I had this problem, but with every Operating System EXCEPT Ubuntu 64-bit (even Debian's stable 32-bit release :O)

Windows XP froze about 5 minutes into the fully loaded operating system (about 7 minutes from boot..), EXCEPT when Sims 2 was in game-play :/.. Figure that one out.. Every other game, application, usually freezes. It's a problem with the video card drivers for my Intel i3 550 processor. 

I'm using a Biostar HD55 MoBo, and 8GB of ram. 

I started with Kubuntu 64-bit- froze (blamed KDE, but I think I was wrong for doing so)
Tried Debian with Gnome- works fine :/. Debian with the stable KDE package froze just like Kubuntu..

Then I tried Ubuntu 64-bit but it kept installing to this stupid failsafe terminal thing... The live CD worked fine, but.. the OS didn't. Finally got Wubi to install.. which I'm not all too thrilled with.. except for the fact it didn't freeze up every few minutes, and actually supports all my ram... (Damn 32-bit desktop laws..)

I ran sudo apt-get update, installed the latest grub loaders, and.. I forget what else.. But I got a GUI out of it and I'm happy. Oh, yeah, I also had to set the root password first. 

Funny.. Not having a GUI is very scary to me.. It's like an expected thing. Ubuntu should have a "Safe Mode" GUI environment instead of a fail-safe terminal, IMHO. Then the Fail-Safe GUI can try to fix the problem. I never figured how the live CD worked fine, whereas after Ubuntu was installed it couldn't even get a simplified GUI :/


**My advice to you**: Figure out if your video driver is the issue.
Also, does it freeze like that on the live CD?

---

### Post by ufukeskici on 2011-03-23
> **cookiecloud said:**
> If you can get to a reasonably stable command prompt, type:

```

lspci

```... and post the output here, or if you can take a (clear) photo of the output from that command and post it here, maybe we can helps ya :-)

Cheers!


Here it is:

-------------
root@UfukEskici:~# lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 06)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 LE [Radeon HD 4800 Series]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
06:00.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
07:01.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
07:05.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
07:07.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
07:09.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
08:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
09:00.0 IDE interface: Device 1b4b:914d (rev 10)
0c:02.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0c:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
root@UfukEskici:~# 
-------------------------

---

### Post by ufukeskici on 2011-03-23
@s-p-n

My problematic Ubuntu is 64-bit :)

Live CD works fine but normal 64-bit Ubuntu OS causes this problem.

---

### Post by ufukeskici on 2011-03-26
I still need help. :(

---

### Post by linuxuser12345 on 2011-03-26
Try installing the latest graphics drivers. Go to "System", "Administration", then "Additional Drivers"

---

### Post by s-p-n on 2011-03-27
Look at this maybe:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

(I poked around, googling your graphics card :) )
"Radeon HD 4800" "ubuntu 64-bit" ati

---

### Post by gandaran on 2011-03-27
> **ufukeskici said:**
> I still need help. :(
do a memory test, the freezes could be due to a lot of things mostly hardware related, see if you can update the BIOS and do the memory test, I have been plagued with the freezes problem over the last two weeks and blaming the updates for it only to finally find out it was a failing memory card after reinstalling Ubuntu for the fourth time.

edit:
if the live cd works but ubuntu freezes after login then updating the BIOS may actually fix the problem.

---

