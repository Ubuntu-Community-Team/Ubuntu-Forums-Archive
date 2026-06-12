---
title: "Getting USB 3.0 running on 10.10"
date: 2010-12-10
forum: General Help
---

### Post by agarzon on 2010-12-10
Hi all,

I just bought some USB 3.0 Drives, and with them some USB 3.0 PCIe cards. Problem is, the cards are not being recognized by Ubuntu.

The manufacturer (ASUS) only posts windows drivers but no Linux support. Some web searches suggest that USB3.0 was inlcuded by default on kernel 2.6.31

Any clues on how to get my PCIe cards recognized and the USB3.0 drives working full speed?

This is the lspci output. The cards show as a SATA controller (Marrvel Technology) The chipset apparently is a NEC 

```

agarzon@euler:~$ lspci
00:00.0 Host bridge: Intel Corporation 5520 I/O Hub to ESI Port (rev 22)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 22)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 22)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 22)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 22)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 22)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 22)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 PCI bridge: Pericom Semiconductor PCI Express to PCI-XPI7C9X130 PCI-X Bridge (rev 04)
03:00.0 VGA compatible controller: nVidia Corporation G96 [Quadro FX 580] (rev a1)
05:00.0 SCSI storage controller: LSI Logic / Symbios Logic SAS1068E PCI-Express Fusion-MPT SAS (rev 08)
06:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe (rev 10)
07:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
07:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
20:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 22)
20:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 22)
20:09.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 9 (rev 22)
20:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 22)
20:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 22)
20:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 22)
22:00.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
23:01.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
23:05.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
23:07.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
23:09.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
24:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
25:00.0 SATA controller: Marvell Technology Group Ltd. Device 9120 (rev 12)
29:00.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
2a:01.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
2a:05.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
2a:07.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
2a:09.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
2b:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
2c:00.0 SATA controller: Marvell Technology Group Ltd. Device 9120 (rev 12)
agarzon@euler:~$ 

```

Manufacturer's specs:
[http://usa.asus.com/product.aspx?P_ID=lGYmelQ8mJvPtYTv](http://usa.asus.com/product.aspx?P_ID=lGYmelQ8mJvPtYTv)

---

### Post by deanjm1963 on 2010-12-10
Which pcie slot did you put the card into? Do you have a 4x slot available?

I have USB3 built into my motherboard - when I have my external (usb3 drive) connected and I open disk utility it says speed is 705mb - I get roughly 5gb of data copied in a minute - 300gb takes just under an hour.

---

### Post by agarzon on 2010-12-10
I have the cards on a 16x slots. The lowest I have is an 8x but is partially blocked by the grapgics card...

---

### Post by deanjm1963 on 2010-12-10
The 16x shouldn't be a problem at all. What kind of transfer speed are you getting?

---

### Post by agarzon on 2010-12-10
None at all. The OS tries to recognize and mount the drives, but they dissapear.

---

### Post by deanjm1963 on 2010-12-10
The drives you bought, have they been formatted yet? Are you using USB3 cables? Any extra info would help, there's no reason why the card and your drives shouldn't be working. Asus is a good brand, never had a problem with anything from them.

---

### Post by agarzon on 2010-12-10
Totally agree on ASUS being a good brand. I just got a wireless card working out the box at home (10.10 32bit OS)

Answering your questions: Yes, I have USB3 cables. The drives do work. I already have plugged and tranfer data to them. I reformatted those to ext4 and work fine on standard USB 2.0 ports.

---

### Post by deanjm1963 on 2010-12-10
This is getting tricky ... hmmm ... I'd be ripping my hair out by now ... what motherboard do you have? You said earlier that your 8x slot was obscured by your video card, another 16x slot?

---

### Post by agarzon on 2010-12-10
Motherboard is an Intel MB labeled as Dell. This is a T7500 workstation. Comes with 5 PCIe slots, 4 of them are 16x and the other is 8x (that's my recollection)

---

### Post by agarzon on 2010-12-10
I guess the question here is:

Can I grab the windows drivers and use them to make it work? similar to what ndiswrapper did for Wireless card drivers?

Or is it possible to build a kernel module for it? If so, how?

---

### Post by deanjm1963 on 2010-12-10
I did a bit of a google and came up with your motherboards pcie specs. 

One PCI-e x16 Gen 2 wired as x4
Two PCI-e x16 Gen 2 slots wired as x8 (one is half length)
Two PCI-e x16 Gen 2 graphics slots
One PCI-X 64bit/100MHz slot with support for 3.3v or universal cards
One PCI 32bit/33Mhz 5V slot

Are both graphics slots used? Your Dell manual should have info on which slot is x4.

USB3 support is built into the kernel - it's not something that's an add-on. The only reason why there are windows drivers is because windows doesn't natively support USB3.

You could try moving the cards around so that the USB3 card ends up in the x4 slot.

---

### Post by agarzon on 2010-12-10
Trying to troubleshoot:

I connected a standard USB 2.0 drive to the card. The USB is present on the "places" menu, but it will not mount. The error I get is: (pic attached)

```
Unable to mount "drive"
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed:
An operation is already pending
```

df -h does not show the device as available for mounting. Neither does the Disk Utility.

---

### Post by deanjm1963 on 2010-12-10
I found this earlier post that might be of some help to you.

[http://ubuntuforums.org/showthread.php?p=7387017]("http://ubuntuforums.org/showthread.php?p=7387017")

---

### Post by agarzon on 2010-12-10
I'll try playing with those. I was trying to access the Dell online manual but I has a couple of problems. Will look at that on Monday since this is my work machine.

deanjm1963 thanks a lot for the help. I'll get back to this thread on Monday. Very little I can do from home. Have a great weekend.

---

### Post by agarzon on 2010-12-10
That is a pretty good thread... may be able to work that one remotely... THANKS!!

---

### Post by agarzon on 2010-12-10
One more thing.

Disk utility does not see the plugged drive, but it does see the SATA Host adapters for both cards.

Maybe I'll remove one of the cards... get it running and then install the second one.. does that make any sense at all?

---

### Post by deanjm1963 on 2010-12-10
Your welcome - hope you can find a fix for the problem.

---

### Post by agarzon on 2010-12-21
I've noticed this post has a lot of hits.

As an update, I have not been able to get these PCI cards running. 

There seems to be a problem with either firmware or drivers for the Marvell SATA controller (both for 9120 and 9123)

I have been looking for potential solutions and at this point the best choice would be to stay away from cards which use these controllers.

If I get something running I'll post an update on this thread

---

### Post by mgscox on 2010-12-21
Not sure if this is the same problem, or not, but I also can't get Ubuntu to boot using USB3 running on an external HDD through a motherboard USB3 connector...

Currently, if I try and boot the HDD via USB3 I get the grub menu, and when I select Ubuntu to boot I get the splash screen and the loading bar(?) indicates activity. However, after a few seconds it drops out to the busybox prompt. Executing a 'ls /dev/disk/by-uuid' (or label, etc) shows that my external USB drive isn't visible.   

Incidentally, fstab is set to boot by UUID so it isn't a case that the drive is being assigned a different identifier, or anything..

However, if I plug the external HDD into a USB2.0 port it boots perfectly (and, of course, is visible under /dev/disk).

Finally, just to make things really interesting, if I boot from a Live CD with the external HDD connected via USB3, then it is visible once the boot has completed and the desktop is available. 

I'm not a linux expert, but it would appear from this that whilst USB3 is supported by the kernel, either the driver isn't being loaded early enough during the bootstrap or it is somehow being disabled, e.g. being powered-off, during the bootstrap process.

---

### Post by gordintoronto on 2010-12-21
> **agarzon said:**
> Hi all,

I just bought some USB 3.0 Drives, and with them some USB 3.0 PCIe cards. Problem is, the cards are not being recognized by Ubuntu.
...
25:00.0 SATA controller: Marvell Technology Group Ltd. Device 9120 (rev 12)



The Marvell 9120 is not a USB 3 device, it's a SATA 3 device. Most of the effort to help you has focussed on USB 3, so it's irrelevant.

Are the drives also SATA 3? Are you trying to set up a RAID configuration?

---

### Post by agarzon on 2011-01-24
gordintoronto, Thanks for chiming in.

You are right: the Marvell SATA adapter is not USB 3.0

Maybe I wasn't clear explainin the hardware. I am talking about a ASUS PCIe Card for USB 3.0 drives. (That's how it is marketed) It is the system the one that shows me this card has a MArvell 9120 Controller.  

The card also features a couple of SATA connectors on the inside portion of it. Also, the system shows it has a USB 3.0 controller. So I guess this is either a SATA card with USB 3 capability or a USB3.0 CArd with SATA capability, or neither, or both!!

Hardware: ASUS U3S6 (Box says USB 3.0 SATA 6G)

About your other question: No, I am not trying to set up a RAID array.

I appreciate if you can shed some light on this matter....

---

### Post by gordintoronto on 2011-01-24
The card is a combo, with two completely separate parts: a SATA 6 GB controller with connectors for two *internal* hard drives, and an USB 3.0 controller with two connectors.

Every time you say SATA, it is not relevant to your problem. You have never posted output from lsusb, which shows usb ports. Newegg isn't currently selling the card, but they do have the specs for it, and pictures! I noticed that they say the card uses AHCI, and that's a technology I have not mastered. You might want to investigate it further; it relates to your motherboard and possibly BIOS settings.

You might also run this command:
sudo lshw > myconfig.txt
then edit myconfig.txt so it only shows USB ports, and post that part here.

---

### Post by hiperjp on 2011-01-27
Hi,
I'm new in this forum.

I'm having issues with my USB 3.0 controller on Ubuntu 10.10, the output of lshw is (deleted the other information):

```

     *-pci
          description: Host bridge
          product: Core Processor DMI
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 memory:f7b00000-f7bfffff
           *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:16 memory:f7bfe000-f7bfffff

```

This mean that I'm having USB 3.0 working in my system?.

I have a Seagate FreeAgent 2TB HDD with his USB 3.0 connector base and cable, and doesn't get recognized in any of the two USB 3.0 that come with the MB, but if I change to another USB 2.0 it's works fine.

I suspect that this USB 3.0 or HDD's implementation it's not being pulled out very well. Even in Windows 7 this HDD doesn't get recognized fast as I connect to a USB 2.0 port.

---

### Post by jimmybute on 2011-01-31
I also need help with this card. Seems like we need to find Linux drivers for it, I thought usb 3.0 support was suppose to be in the latest kernels. hmmm

Please post if anybody finds a fix for the ASUS U3S6 card

---

### Post by agarzon on 2011-02-11
hiperjp,

It seems you have the same NEC USB 3.0 controller I have on my pci card.

Are your usb 3.0 ports on the MB or a separate PCIe card?

Windows does not have any native support of USB 3.0 like linux has and requires for drivers to be installed.

Do any standard USB 2.0 drives work on your USB 3.0 ports?

As gordintoronto suggested, try an lsusb command to see if your card is listed as a usbdevice

As an update, I have not had any success so far in getting the U3S6 card working on my system.

---

### Post by wiz-oz on 2011-06-11
Did anyone ever get this to work?

I have bought a 1T bus powered usb3 disk, and added a nec usb3.0 pci-1x card to my linux box.

What puzzles me is that if I do a lsusb the device does not show up:

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

(manually loading xhci_hcd says bus number is 8.

If I do usb-devices the device does show up:

```
T:  Bus=08 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=02.06
S:  Manufacturer=Linux 2.6.35-28-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:02:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
```

Has anyone an idea how to get this working?

cheers,

Wiz

---

### Post by 3rdalbum on 2011-06-11
Funny - I was going to ask the OP if this is a bus-powered device, or a self-powered device. The device appearing and then disappearing sounds a bit like the device is not getting enough power. It could be one of a couple of other things, though.

---

