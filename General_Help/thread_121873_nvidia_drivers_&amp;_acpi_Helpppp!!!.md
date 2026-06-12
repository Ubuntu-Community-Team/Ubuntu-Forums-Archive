---
title: "nvidia drivers &amp; acpi Helpppp!!!"
date: 2006-01-26
forum: General Help
---

### Post by ptrbee on 2006-01-26
:confused: [-o< 

Can **anyone** help me... I have a toshiba qosmio f10 notebook, currently i'm using fc4 on it but after testing ubuntu recently i would like to use it. A few problems plague me though. lm-sensors do  not work for me in ubuntu, acpi does not work correctly so my fans are either always on or off :confused: as they both work in fc4.and the nvidia 8178 drivers do not work everytime i install them i get a black screen on reboot. I've benn frantically trying distro's hoping that everything would work on at least 1x & while trying archlinux yesterday i came across this "gdm[2621]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0"  If you need anymore info let me know,my nvidia bug report is attached &  i've posted stuff here [http://www.nvnews.net/vbulletin/showthread.php?t=63158&page=2&highlight=black+screenbut](http://www.nvnews.net/vbulletin/showthread.php?t=63158&page=2&highlight=black+screenbut)
 my lspci output is :
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX Go5700] (rev a1)
02:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:0b.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:0b.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:0b.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:0b.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

Peter.

---

### Post by rjwood on 2006-01-26
Did you get 'xserver' error message? Did you install Breezy-Hoary- or Dapper? If Dapper, you may want to instead go with one of the other 2 (probably breezy). How did you install the driver? See this thread General - HOWTO: Latest NVIDIA drivers - Ubuntu Forums
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia).

or you can alway's do this Automatix (Automated GUI installation script) - Ubuntu Forums
[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=nvidia)

Good Luck and Have fun!!

---

### Post by ptrbee on 2006-02-01
Hi RJwood,
I tried both Breezy & dapper, i also followed that guide to install but no errors once the system locks. On other distros i can ssh into my system but cannot ssh in ubuntu. Pleas note I am running 7676 driver at the moment.

Peter.

---

