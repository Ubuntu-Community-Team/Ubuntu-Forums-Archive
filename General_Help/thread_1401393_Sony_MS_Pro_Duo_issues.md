---
title: "Sony MS Pro Duo issues"
date: 2010-02-08
forum: General Help
---

### Post by nishant.singh28 on 2010-02-08
I have a Sony Cybershot DSC W210. It uses a Sony MS Pro Duo. I have a multi card reader in my laptop that can read MS Pro. In Windows, I could simply plug the ProDuo attached to its adapter into the reader and it would work fine. In Ubuntu, the card reader works. I've used SD cards in it. But the MS ProDuo is not even detected. I have been Googling and trying different things for the last 3 months but to no avail :(. Now I have to go for a trip in a couple of weeks and I don't want to carry the bulky camera cable along. Is there any way to get the card reader to mount the ProDuo?
lspci:
```
nishant@nishant-Studio:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

---

### Post by nishant.singh28 on 2010-02-08
BUmp!!!

---

### Post by nishant.singh28 on 2010-02-18
Buuuuuuuuuummmmmmppppppp!!!!!!!!!!

---

### Post by dvn3ch on 2010-02-19
Sorry to say, but I have been doing the same thing for my older Sony Vaio laptop 'FRV series'.  This laptop has a built in Sony Memory Stick Pro reader but will not read Pro's or Duo's w/adaptor.

Surprising to me was that I hooked up a USB device that reads 7-in-1.  It will read MMC, SD, and SDHC (that I have personally tested) but will not read the MS Pro or Duo.  And as much as I hate to do it, I go virtual with XP (or Win7) and use the external reader mounted through my VM (Virtualbox 3.1).  Here Windoze apparently recognises the card and will let me read and write from it.

I hate doing that because it is a complete pain in the ****.  I hate to use Win*** anything that is why all my systems have been switched to Linux for over a year now and I will never look back.  So this is why I, too, have been looking high and low for a solution to my problem.  I am going to assume it is a driver problem related to the kernel of Linux since Windoze will recognise it even in a VM.  

I may consider emailing Sony to see if a patched up driver is available for Linux.  Good luck and PM me if you find a solution (and I will do the same).
:)

---

### Post by antaresca on 2010-04-14
same problem any solution?

---

### Post by nishant.singh28 on 2010-10-07
Finally, a solution.
Mind you, this works for Kernels 2.6.32+. I'm using 2.6.35 in Maverick RC.
This is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208")

This is the driver package:
[https://bugs.launchpad.net/opensuse/+bug/238208/+attachment/1506369/+files/memstick-v2.tar.bz2]("https://bugs.launchpad.net/opensuse/+bug/238208/+attachment/1506369/+files/memstick-v2.tar.bz2")

Download it, extract, then:```
make
sudo make install
sudo make load
```
The card is detected but won't mount automatically. When you click on it, it will mount. Read write works perfectly.

---

### Post by Viglen on 2013-01-15
Does this also apply to kernel 3.5?

---

### Post by nishant.singh28 on 2013-01-15
I don't know for sure. That camera went kaput, so I haven't used this driver for ages. I read somewhere that it was integrated into the kernel now. If it isn't integrated, you can try installing it. Method should remain the same.

---

### Post by Viglen on 2013-01-15
Thanks for replying, it's been 3 years almost. 
Anyway sorry I'm a bit new to this and I get an error on the first make step

> 
~/Downloads/memstick $ make
make -C /lib/modules/3.5.0-17-generic/build M=/home/adam/Downloads/memstick
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  LD      /home/adam/Downloads/memstick/built-in.o
  LD      /home/adam/Downloads/memstick/core/built-in.o
  CC [M]  /home/adam/Downloads/memstick/core/memstick.o
/home/adam/Downloads/memstick/core/memstick.c:24:27: error: expected &#8216;)&#8217; before &#8216;uint&#8217;
/home/adam/Downloads/memstick/core/memstick.c:213:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:213:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:213:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:245:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:245:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:245:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:259:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:259:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:259:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:284:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:284:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:284:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:317:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:317:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:317:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:385:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:385:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:385:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:402:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:402:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:402:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:423:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:423:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:423:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:458:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:458:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:458:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:469:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:469:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:469:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:486:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:486:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:486:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:612:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:612:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:612:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:645:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:645:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:645:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:666:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:666:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:666:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:677:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:677:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:677:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:689:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:689:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:689:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:707:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:707:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:707:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:715:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:715:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:715:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:721:1: warning: data definition has no type or storage class [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c:721:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/adam/Downloads/memstick/core/memstick.c:721:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c: In function &#8216;memstick_init&#8217;:
/home/adam/Downloads/memstick/core/memstick.c:728:2: error: implicit declaration of function &#8216;create_freezeable_workqueue&#8217; [-Werror=implicit-function-declaration]
/home/adam/Downloads/memstick/core/memstick.c:728:12: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/adam/Downloads/memstick/core/memstick.c: At top level:
/home/adam/Downloads/memstick/core/memstick.c:756:15: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/adam/Downloads/memstick/core/memstick.c:757:16: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/adam/Downloads/memstick/core/memstick.c:758:20: error: expected declaration specifiers or &#8216;...&#8217; before string constant
cc1: some warnings being treated as errors
make[3]: *** [/home/adam/Downloads/memstick/core/memstick.o] Error 1
make[2]: *** [/home/adam/Downloads/memstick/core] Error 2
make[1]: *** [_module_/home/adam/Downloads/memstick] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [build] Error 2



---

### Post by nishant.singh28 on 2013-01-15
Are you sure the system does not recognise the Memory Stick automatically? It is supposed to.
Can you dump lspci here? Just run
```
lspci
``` 
and show us the dump.

---

### Post by Viglen on 2013-01-15
Pretty sure, when putting in an SD the folder automatically opens.  Nothing happens when putting in the Pro Duo card
below is lspci while both cards are inserted.

> 
~ $ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 (rev 34)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)



---

