---
title: "How can I see the contens of a SmartMedia/xD card?"
date: 2010-04-11
forum: General Help
---

### Post by welshmike on 2010-04-11
When I insert my Olympus camera xD card in the built-in card reader of my laptop I have no idea how to see the content.
How may I do this please?

dmesg shows SmartMedia/xD card detected in socket 0:2

(I'm running Ubuntu 9.10)

---

### Post by ajgreeny on 2010-04-11
Normally it is automounted and appears as an icon on your desktop and a nautilus window pops up.  If that is not happening, have a look in **/media** to see if there is a folder showing with an appropriate name for the card.

Otherwise I can't imagine what is going on here, an xd card surely shows up in that way on my wife's compaq CQ70 laptop with a built-in card reader.

---

### Post by welshmike on 2010-04-11
I had a look at /media:

mike@mike-laptop:~$ dir /media
cdrom  cdrom0
mike@mike-laptop:~$

Maybe there's a hardware problem. I'll boot with Windoze XP and see what happens.

---

### Post by welshmike on 2010-04-11
No hardware problem. Device opened on XP automatically as a disk. Hardware devices said SD host controller.

What next I wonder?

---

### Post by ajgreeny on 2010-04-11
Plug it in, run ```
sudo fdisk -l
``` and note the device name.  Make a new folder to mount it with ```
sudo mkdir /media/xdcard
``` Now use the command ```
sudo mount /dev/sdx -t vfat /media/xdcard
```changing the sdx to whatever fdisk shows, and the filesystem type (vfat) if it is not a fat32 or fat16 card.  If any errors show, report them back here.

---

### Post by welshmike on 2010-04-13
Unfortunately the plugged in xd card does not show:
 
mike@mike-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x323c513c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4667    37487646    7  HPFS/NTFS
/dev/sda2            4668        7296    21117442+   f  W95 Ext'd (LBA)
/dev/sda5            4668        7181    20193673+  83  Linux
/dev/sda6            7182        7296      923706   82  Linux swap / Solaris
mike@mike-laptop:~$

Edit1: Maybe there is no driver for the xd card reader. I'll boot with XP and find out the make of the xd card reader. Back soon.

Edit2: mike@mike-laptop:~$ lspci -v  #shows <access denied>. I wonder why?
.
.
.
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
	Subsystem: Toshiba America Info Systems Device ff03
	Flags: bus master, medium devsel, latency 57, IRQ 19
	Memory at b0109400 (32-bit, non-prefetchable) [size=256]
	Memory at b0109000 (32-bit, non-prefetchable) [size=256]
	Memory at b0106400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

---

### Post by sykoken on 2010-04-17
has there been any discoveries made on this?  i'm having the same issue with our Olympus xD card as well.
thanks!

---

### Post by matt-fender on 2010-06-21
Also having same problem, SD cards work just fine but XD is dead as a dodo, dmesg shows absolutely nothing.:confused:

---

### Post by bluefoxox on 2010-09-06
I am working on a fix, and have made headway on my own machine.  Can you run lspci and look for a JMicron controller?  If you find one I may be able to help.

---

### Post by welshmike on 2010-09-06
> **bluefoxox said:**
> I am working on a fix, and have made headway on my own machine.  Can you run lspci and look for a JMicron controller?  If you find one I may be able to help.

No JMicron controller here:

```
mike@mike-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
mike@mike-laptop:~$ 

```

---

