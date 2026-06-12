---
title: "Ubuntu 12.04 LTS Randomly freezes"
date: 2012-08-03
forum: General Help
---

### Post by oKzrh on 2012-08-03
Hi guys.
I'm using Ubuntu 12.04 LTS 32bit.
What happens is, whenever I'm doing something.. Surfing the web, installing softwares, just every normal thing, my PC just randomly freezes sometime and I have to restart my computer.
Why is it happening?
I just installed Ubuntu again, It's a fresh installation, and It's still doing that.
Please help me!
Thanks.

---

### Post by FatFrog on 2012-08-03
The next time your comp freezes, hit CTRL+ALT+F1 to swith to TTY1. then run the 'top' command. This'll bring up a list of running processes.

Is something pegging the CPU? If so , what?

---

### Post by Ubun2to on 2012-08-03
Lets get some specs before we throw random ideas that could mess up everything.
Please execute these commands in terminal and post the output here:
```
lspci
lsusb
uname -v
uname -p
hwinfo
```
This is what each command does:
lspci-lists all the PCI devices attached to the computer. This is useful in diagnosing display problems if you use a PCI video card, and is also useful for diagnosing other PCI card problems (like Ethernet, USB 3.0 cards, and expensive audio cards for composers).
lsusb-lists all USB devices attached to the computer. This is useful for identifying USB devices that have bugs in the drivers or are incompatible.
uname -v-lists the version of the Linux kernel that you have. Sometimes, it's a problem with the kernel, and you just have to wait for new releases of the kernel with new drivers.
uname -p-lists the processor type. It is easy to accidentally install the wrong version of Ubuntu. Installing 32 bit on a 64 bit machine, for example, makes any OS suck (it's slow, laggy, and doesn't work well). Same thing applies to installing 64 bit on 32 bit machines, only nothing will work, as the 32 bit architecture is totally different from the 64 bit architecture.
hwinfo-lists all the hardware in your computer. This is useful for finding hardware that is not compatible with Ubuntu or requires extra drivers.
Also, for good measure, please list the manufacturer and name of the computer. This is usually listed somewhere around the keyboard on a laptop, and on or around the Microsoft service tag on desktops.

---

### Post by oKzrh on 2012-08-04
> 
orel@orel-MS-7522:~$ lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 12)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 12)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 12)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 12)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 12)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 12)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 12)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 12)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
02:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce 9800 GT] (rev a2)
05:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
05:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
07:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 10)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
orel@orel-MS-7522:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 3938:1031  
orel@orel-MS-7522:~$ uname -v
#43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012
orel@orel-MS-7522:~$ uname -p
i686
orel@orel-MS-7522:~$ hwinfo
The program 'hwinfo' is currently not installed.  You can install it by typing:
sudo apt-get install hwinfo
orel@orel-MS-7522:~$ 

Intel Core i7 920 - 2.6Ghz
Geil 3GB DDR3
NVIDIA GeForce 9800GT 512MB

---

### Post by oKzrh on 2012-08-04
It just froze again, and I wasn't even able to press Ctrl+Alt+F1.

---

### Post by Ubun2to on 2012-08-04
I mean to say uname -a, not uname -v. I also forgot that hwinfo is not included with Ubuntu-I install it on every computer I own, so I forgot. Sorry about that.
Anyway, the most suspicious looking thing looks like the NVidia card. The rest of the devices appear to be manufacturers that support Linux. Your i7 was the first generation, and the i7 shows up on the Ubuntu Supported Hardware list.
If you haven't already, make sure that the NVidia drivers are active via the Additional Drivers program.

---

