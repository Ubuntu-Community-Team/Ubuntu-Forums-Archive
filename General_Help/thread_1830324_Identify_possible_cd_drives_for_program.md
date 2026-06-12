---
title: "Identify possible cd drives for program"
date: 2011-08-21
forum: General Help
---

### Post by medusa569 on 2011-08-21
In windows one could identify the drive by letter..easy...but in merrkat I need to identify and augment a file that allows the start up location of information for a program in either of my 2 cd drives. One is the internal cd floppy and I have a second that is usb connected a cd/dvd. I would like either one to be "seen " as the possible source for the necessary information".  How do i write that into a file?? The sample file I am changing is below.....

All; d:\caycedat\indx;d:\caycedat\text;d:\caycedat\bgrd;d:\caycedat\rept Background;d:\caycedat\bgrd Index;d:\caycedat\indx Reports;d\caycedat\rept Text;d\caycedat\text

thank you in advance....:confused:

medusa

---

### Post by dino99 on 2011-08-21
open a terminal and run: sudo lspci

---

### Post by medusa569 on 2011-08-21
> **dino99 said:**
> open a terminal and run: sudo lspci

  here  is the output from that command.....


00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
02:0a.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
02:0b.0 USB Controller: NEC Corporation USB (rev 43)
02:0b.1 USB Controller: NEC Corporation USB (rev 43)
02:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
02:0c.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax Modem (rev 08)
02:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
02:0d.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)

---

