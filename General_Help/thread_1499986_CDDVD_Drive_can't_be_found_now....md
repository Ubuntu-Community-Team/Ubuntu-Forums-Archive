---
title: "CD/DVD Drive can't be found now..."
date: 2010-06-02
forum: General Help
---

### Post by jjloupe on 2010-06-02
Upgraded from 9.10 to 10.04...using the CD Drive.  Today I find out that the CD/DVD Drive is not recognized.   output from lspci: 


0:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:08.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax/Voice/Spkp Modem (rev 01)
02:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

output from dmesg|grep CD:

    0.600187] ata2.00: ATAPI: SAMSUNG CDRW/DVD SM-308B, T100, max MWDMA2
[    1.033197] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SM-308B T100 PQ: 0 ANSI: 5
[    1.039846] Uniform CD-ROM driver Revision: 3.20
[    1.040088] sr 1:0:0:0: Attached scsi CD-ROM sr0


 Let me know if you need any more info. Like I said it was operational before I upgraded, but haven't used it since 10.04 was released, so I can't say exactly when it stopped working.

---

### Post by roquet on 2010-06-04
Maybe it's a bug [COLOR="Red"]([link)]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/562092")[/COLOR]

---

### Post by jjloupe on 2010-06-04
no, I don't have the same symptoms. 

However I opened disk  utility, and it shows the drive, but does not detect media. If I click the "eject" buttton, I get an error saying no media detected.

---

### Post by jamiebscott on 2010-06-06
Same deal, ie. dvd doesn't mount and Disk Utility just says "Media not detected". And this is on a fresh, clean install of Ubuntu 10.04. What's with that?

---

### Post by jjloupe on 2010-06-06
I know there has to be an answer....anyone??

---

### Post by jjloupe on 2010-06-09
Wow...I as told about the great community support with Ubuntu. Where is it? I am not the only one with this problem. 

I need my optical drive back. Help please.

---

