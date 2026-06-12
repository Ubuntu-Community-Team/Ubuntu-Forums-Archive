---
title: "How should i install my modem?"
date: 2009-08-30
forum: General Help
---

### Post by sinakr on 2009-08-30
hello guys.i have the following dial up modem:

D-Link DFM-562IS HSFi PCI Modem

how should i install my device on ubunto 9.4?
big thanks already

---

### Post by sinakr on 2009-08-30
please i need help with that.

---

### Post by P4man on 2009-08-30
Its a so called "win modem" or soft modem.. If it doesn't work out of the box, its probably not worth trying. you can pick up external hardware modems for 1$ on ebay.

if you must try (eg if its a modem built in a laptop), you can try this:

[http://ubuntuforums.org/showthread.php?t=308098](http://ubuntuforums.org/showthread.php?t=308098)

dont have too much hope though.

---

### Post by sinakr on 2009-08-30
i find this:
[http://gratis-tis.blogspot.com/2008/02/d-link-dfm-562is-and-du-562m-ubuntu.html](http://gratis-tis.blogspot.com/2008/02/d-link-dfm-562is-and-du-562m-ubuntu.html)

i hope it works.
i have another question.how should i go to terminal?
cause i never worked with linux before.
thanks

---

### Post by P4man on 2009-08-30
that how-to is incomplete, and if you've never used linux or a terminal before, what you're attempting is gonna be.. hard. Also be aware the linuxant drivers are not freeware. They have a "trial" version that limits you to 14.4k speeds, you need to pay for the full speed version,and that is assuming you'd get it to work. I dont know about you, but I think the idea of having to pay for a driver is simply outrageous.

you can have a look at this page:

[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

It mentions Dell drivers which are free and might work, but it looks like a horrible mess to me.

Really, I think you're better off buying another modem.

---

### Post by sinakr on 2009-08-30
> **P4man said:**
> that how-to is incomplete, and if you've never used linux or a terminal before, what you're attempting is gonna be.. hard. Also be aware the linuxant drivers are not freeware. They have a "trial" version that limits you to 14.4k speeds, you need to pay for the full speed version,and that is assuming you'd get it to work. I dont know about you, but I think the idea of having to pay for a driver is simply outrageous.

you can have a look at this page:

[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

It mentions Dell drivers which are free and might work, but it looks like a horrible mess to me.

Really, I think you're better off buying another modem.



thanks buddy.i will try that.but currently i dont have money to buy a new modem.

---

### Post by tempus on 2009-08-30
I recommend a US Robotics USB modem, model: 5637. Works right out of the box, no drivers needed. I use Gnome-PPP to dial out. good luck. you may need to set permissions for some files.

---

### Post by P4man on 2009-08-30
Ask around. I dont know where you live, but in most places, ppl will still have a POTS (Plain Old Telephone System) modem laying around gathering dust and they should be happy to give away to someone who can use it. 

Id offer to send you one of mine, but I fear I threw them away years ago. You can find them on ebay for $1,just look for cheap shipping.
 
Or perhaps someone else reading this wants to donate a 56k modem ? :)

---

### Post by sinakr on 2009-08-30
> **P4man said:**
> Ask around. I dont know where you live, but in most places, ppl will still have a POTS (Plain Old Telephone System) modem laying around gathering dust and they should be happy to give away to someone who can use it. 

Id offer to send you one of mine, but I fear I threw them away years ago. You can find them on ebay for $1,just look for cheap shipping.
 
Or perhaps someone else reading this wants to donate a 56k modem ? :)

you know in my country for $1 even nobody gonna spit in your face.here a 56K external modem is at least $50.and im just a collegian and currently i cant spend my money for buying that stuff.so i have no option but using my internal modem.i checked my modem by modem scan.here is its report:





 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.28-11-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=x86_64,  
Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009
 scanModem update of:  2009_08_15

The dialer utility package WVDIAL does not appear to be installed on your System. 
For Ubuntu Jaunty users, there are at the bottom of [http://linmodems.technion.ac.il/packages/:](http://linmodems.technion.ac.il/packages/:)
     wvdial_jaunty_amd64.zip   for x86_64, 64 bit bus systems.
     wvdial_jaunty_i386.zip    for 32 bit systems.
These are about 1 MB in size.  After downloaded and copied into your Linux partition:
$ unzip wv*.zip
Within the new folder:
$ sudo dpkg -i *.deb
will  complete the wvdial installation
Please read Modem/DOCs/wvdial.txt for usage information.

Some modem drivers can only be used in 32 bit modem on x86_64 systems,
while some others are competent on x86_64 Systems.  Cases are:
1) [http://linmodems.technion.ac.il/bigarch/archive-seventh/msg03119.html](http://linmodems.technion.ac.il/bigarch/archive-seventh/msg03119.html) 
for the snd-hda-intel audio+modem driver. Also applicable to AC97 modem controllers.
In both cases, 32 bit libraries must be installed to support the slmodemd helper having a precompiled 32 bit component.
2) For USB modems using the slusb.ko driver. 32 bit libraries must be installed to support the slmodemd helper having a precompiled 32 bit component
3) The hsfmodem and hcfpcimodem drivers for Conexant chipsest modes are x86_64 competent.

 There are no blacklisted modem drivers in /etc/modprobe*  files 
 Potentially useful modem drivers now loaded are:
         snd_hda_intel       

Attached USB devices are:
 ID 09da:000a A4 Tech Co., Ltd Port Mouse
If a cellphone is not detected, see [http://ubuntuforums.org/archive/index.php/t-878554.html](http://ubuntuforums.org/archive/index.php/t-878554.html)
A sample report is:  [http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html](http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html)

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [email]discuss@linmodems.org[/email]

For candidate card in slot 03:07.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 03:07.0	14f1:2f30	14f1:20d5	Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem 

 Modem interrupt assignment and sharing: 
 --- Bootup diagnostics for card in PCI slot 03:07.0 ----
[    0.352408] pci 0000:03:07.0: reg 10 32bit mmio: [0xfbff0000-0xfbffffff]
[    0.352415] pci 0000:03:07.0: reg 14 io port: [0xec00-0xec07]
[    0.352455] pci 0000:03:07.0: PME# supported from D3hot D3cold
[    0.352460] pci 0000:03:07.0: PME# disabled

 The PCI slot 03:07.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

For candidate card in slot 00:14.2, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:14.2	1002:4383	1043:8346	Audio device: ATI Technologies Inc SBx00 Azalia 

 Modem interrupt assignment and sharing: 
 16:         14      10175   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb4, HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:14.2 ----
[    0.351905] pci 0000:00:14.2: reg 10 64bit mmio: [0xf7ff4000-0xf7ff7fff]
[    0.351936] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.351940] pci 0000:00:14.2: PME# disabled
[    9.597242] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16

 The PCI slot 00:14.2 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.20
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-00: VT1708B Analog : VT1708B Analog : playback 2 : capture 2
00-01: VT1708B Digital : VT1708B Digital : playback 1

about /proc/asound/cards:
------------------------
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf7ff4000 irq 16

 PCI slot 00:14.2 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko
UNEXPECTED HDA diagnostic outcome.
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 03:07.0:
	Modem chipset  detected on
NAME="Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem "
CLASS=0780
PCIDEV=14f1:2f30
SUBSYS=14f1:20d5
IRQ=10
IDENT=hsfmodem
Driver=hsfmodem-drivers

 For candidate modem in:  03:07.0
   0780 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem 
      Primary device ID:  14f1:2f30
 Support type needed or chipset:	hsfmodem
 


For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt

 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.80.02.02full_k2.6.28_11_generic_ubuntu_i386.deb.zip 
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See DOCs/Testing.txt  for details.
 
 The directions following below need only be pursued, if the above procedures are not adequate.

Start at [http://www.linuxant.com/drivers/hsf/downloads-license.php](http://www.linuxant.com/drivers/hsf/downloads-license.php) to find the
hsfmodem package matching your System. For several Linux distros, there are
precompiled drivers matched to specific kernels. These have within the FileName,
your KernelVersion:	2.6.28_11_generic
They can be found through [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) 
A more precise location may be given a few paragraphs below.
If an EXACT Match with your your KernelVersion is not found, one of the 
"Generic packages with source" near the bottom of the page must be used.
Downloaded packages must be moved into the Linux partition (home folder is OK)
and unzipped with:
	unzip hsf*.zip
The installation command for a .deb suffic packages is, with root/adm permission:
  sudo dpkg -i hsf*.deb
while for .rpm suffix it is, with:
  rpm -i hsf*.rpm
 Read DOCs/Conexant.txt

Writing DOCs/Conexant.txt



Predictive  diagnostics for card in bus 00:14.2:
	Modem chipset not detected on
NAME="Audio device: ATI Technologies Inc SBx00 Azalia "
CLASS=0403
PCIDEV=1002:4383
SUBSYS=1043:8346
IRQ=16
HDA=1002:4383
SOFT=1002:4383.HDA


 High Definition Audio (HDA) cards MAY host a modem chip in their Subsystem, 
 and many are supported by the ALSA audio+modem driver snd-hda-intel
 A modem was not detected on HDA card 1002:4383.
 If another modem card is present, then most likely 1002:4383 does not host a modem.
 If another modem card has not been detected, then possibilities are:
	1) A Conexant modem chip is present on 1002:4383, as Conexant chips
 are frequently not detectable by ALSA diagnostics
	2) The modem may be of the older non-PCI Controller Chipset (hardware) type.
Try detection with Root permission:
	sudo wvdialconf  /etc/wvdial.conf

 For candidate modem in:  00:14.2
   0403 Audio device: ATI Technologies Inc SBx00 Azalia 
      Primary device ID:  1002:4383
    Subsystem PCI_id  1043:8346 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 
                        
      

Support type needed or chipset:	

Support can likely be achieved through two mutually exclusive alternatives:
1) The hsfmodem software for Conexant chipset modems: Read DOCs/Conexant.txt
The following ALSA alternative CANNOT work with Conexant modems.

2) An ALSA modem driver plus slmodemd.  Read DOCs/Smartlink.txt for details, and
to test get the package SLMODEMD.gcc4.3.tar.gz from:
	[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)

Writing DOCs/Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.3.3
             and the compiler used in kernel assembly: 4.3.3

 The patch utility is needed and is needed for compiling ALSA drivers, and possibly others. 

 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.3
   linuc_headers base folder /lib/modules/2.6.28-11-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------





please can u help me install my modem.

---

