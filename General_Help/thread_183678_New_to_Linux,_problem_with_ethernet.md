---
title: "New to Linux, problem with ethernet"
date: 2006-05-28
forum: General Help
---

### Post by legendarysock on 2006-05-28
Hey everybody

I recently downloaded Ubuntu 5.10, and I want to switch over from Windows to Linux eventually, mainly for the programming and open source advantages. However, I'm not to sure I'm ready to give up Windows so I installed it on my old Compaq Deskpro. Everything went well, except it said no ethernet interface was detected. I'm new the whole concept of Linux, so I'm not sure exactly what to do first to diagnose the problem. Any help is greatly appreciated.

- Karan

---

### Post by chrestomanci on 2006-05-28
I assume there is an ethernet card, that works under windows.

* As root, run 'lspci -v' to list PCI devices. Is your network card there? does the kernel give it a sensible name, or just numbers?

* Try googling the name you get with "Linux driver". Find anything?

* Knoppix is very good a auto detecting stuff, so you could try booting your box with a knoppix disc, and if it finds your card, taking down the settings it uses, and transfering them to Ubuntu

* You could also google for your PC model name & linux support.

---

### Post by legendarysock on 2006-05-28
Thanks for the quick reply.

Of course, there is an ethernet card and if I connect it to my router, a light on my router turns on, notifying me that there is power being sent into the ethernet device and its detected by the computer itself (i think, correct me if i'm wrong). Sadly, I bought this computer without an OS and I never ran Windows on it. It kind of sat in the corner of my room for a long long time until I found Linux.

Onto what you said:

In the terminal, i did sudo (your command) and got a whole bunch of mangled information. I don't exactly know what kind of ethernet card I have. Among the information was Host bridge, PCI bridge, ISA Bridge, IDE interrface, USB controller (all intel corp), then a vga compatible controller, and something else that I'm not to sure of. it says Bridge: Intel Corp and something about acpi at the end. Sorry about the vague information.

I also just downloaded Knoppix and burned a copy, I'm going to try it now. I don't exactly know what model my PC is, but I'm sure I can find it. Thanks for the help again.

- Karan

---

### Post by chrestomanci on 2006-05-28
Sounds like your PC has an Intel chipset, Perhaps you should post the output from lspci here so we can see.

It should be fairly easy to get drivers for ethernet on an Intel chipset, as they are very common.

Another possibility is that the card has been detected, but a firewall is stopping you using it. Have you checked?

Another possibility is a udev screw-up, but if you are running a vanilla system that would be unlikely.

---

### Post by legendarysock on 2006-05-29
Alright, sorry I took so long.
- I tested my system with Knoppix 4.0 and I was still unable to connect to the internet, and I assume this problem is still originating from the ethernet interface problem (by the way, its an ethernet card connected via PCI, not integrated on the motherboard)
- Here is the results from the lspci:

> 0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at 44000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [a0] AGP version 
1.0

0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32

        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 40000000-410fffff

0000:00:14.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0


0000:00:14.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at 2060 [size=16]

0000:00:14.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])

        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 2040 [size=32]

0000:00:14.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9


0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Rage Pro Turbo AGP 2X
        Flags: bus master, stepping, medium devsel, latency 66, IRQ 11

        Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 1000 [size=256]
        Memory at 41000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [50] AGP version 1.0

Look forward to your reply.
- Karan

---

### Post by RRS on 2006-05-29
I think you may find [this guide]("http://www.ubuntuforums.org/showthread.php?t=87643") helpfull.

Post back with results or further questions.

---

### Post by legendarysock on 2006-05-29
Thanks for the link to the guide.
However, I've had no luck with any of the things in the guide.

1. I tried sudo mii-tool eth0 and it said that it failed, saying there was no such device. i also tried eth1, eth2, etc, hoping for something. nothing. ](*,) 

2. I tried ifconfig eth0 and it said there was an error fetching interface information and device not found.

3. I tried lspci | grep Eth/grep mii but neither did anything.

---

### Post by RRS on 2006-05-29
Odd, even without a driver I would expect the system to at least find/see the card.

Would it be a major problem for you to open the case and remove the card? It should be labeled with a Mfg model name/number. This would ensure a proper search for the correct driver.

Also the physical removal and reinsertion may solve any poor connection problems if the computer has been sitting around unused for sometime.

Does the computer you're on the net with now have a PCI card or is the nic on the motherboard? If it's a card you might try swapping it into the Ubuntu machine and testing for a connection with it. Even though you're getting the LED indicators the card still may not be fully functional.

Let us know, we'll get you online yet.

---

### Post by legendarysock on 2006-05-30
The PC I'm on right now is fairly new, and I don't trust myself with opening it. Besides, the ethernet interface is integrated into the motherboard on this computer.

I will open up the computer to check what kind of Ethernet card is connected to it, but I first have to find out how exactly to open it... damn non-standard form factors.

EDIT:
Alright heres the deal:
- I opened up the computer and found it was a Compaq 116188-001 NIC, which I hear is the Intel PRO/100+ card located in one of the PCI slots
- Here is some information about it: [http://support.intel.com/support/network/adapter/pro100/pro100plus/](http://support.intel.com/support/network/adapter/pro100/pro100plus/)
- The NIC turned out to be loose, so I stuck it back in properly and I'm just about to go test it now.

EDIT 2:
Ok, in the end, it turns out that the card was loose. However, I'm still having problems connecting to the Internet. I'm going back to the guide you gave me to try some things out (by the way, sudo mii-tool eth0 is negociated and the link is ok). Thanks again, I'll post back with results.

---

### Post by legendarysock on 2006-05-30
WOOHOO i love you i love you i love you (heterosexually). I used the guide, had some problems, but it worked perfectly afterwards. I'm posting this from my Ubuntu PC now!

---

### Post by RRS on 2006-05-30
Congratulations and welcome to Ubuntu :)

Glad I could be of some small assistance, most of my limited knowledge has come from browsing these forums while trying to fix my own screwups.

---

