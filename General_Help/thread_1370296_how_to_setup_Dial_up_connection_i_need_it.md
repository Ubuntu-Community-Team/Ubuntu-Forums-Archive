---
title: "how to setup Dial up connection i need it"
date: 2010-01-02
forum: General Help
---

### Post by ibrahim.k on 2010-01-02
Hi,
For some reasons i can only use dial up connection can you please help to know how to create a dial up connection and setup the modem driver guides weren't so helpful
I have hp-dv6 1045
this is the modem data




 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.31-16-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009
 scanModem update of:  2009_12_10


The dkms driver upgrade utilities are installed,

 There are no blacklisted modem drivers in /etc/modprobe*  files 

 Potentially useful modem drivers now loaded are:
       snd_hda_intel           

Attached USB devices are:
 ID 05c8:010f Cheng Uei Precision Industry Co., Ltd (Foxlink) 
 ID 09da:000a A4 Tech Co., Ltd Port Mouse
 ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
If a cellphone is not detected, see [http://ubuntuforums.org/archive/index.php/t-878554.html](http://ubuntuforums.org/archive/index.php/t-878554.html)
A sample report is:  [http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html](http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html)

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [email]discuss@linmodems.org[/email]

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 00:1b.0    8086:293e    103c:3629    Audio device: Intel Corporation 82801I 

 Modem interrupt assignment and sharing: 
 22:      92046      75385   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[    0.331695] pci 0000:00:1b.0: reg 10 64bit mmio: [0xdd000000-0xdd003fff]
[    0.331746] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.331750] pci 0000:00:1b.0: PME# disabled
[   27.244105] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   27.244134] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   27.385332] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   27.396889] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   27.396940] input: HDA Intel Line Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12

 The PCI slot 00:1b.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.21
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 1
00-01: STAC92xx Digital : STAC92xx Digital : playback 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdd000000 irq 22

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: LSI ID 1040
Address: 1
Function Id: 0x2
Vendor Id: 0x11c11040
Subsystem Id: 0x103c137e
Revision Id: 0x100200
Modem Function Group: 0x1

 The audio card hosts a softmodem chip:  0x11c11040
If not a Conexant modem, the driver agrsm with its dependent drivers:

----------
provide audio + modem support with the modem chip residing on the subsystem.
Any particular card can host any one of several soft modem chips. 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:1b.0:
    Modem chipset  detected on
NAME="Audio device: Intel Corporation 82801I "
CLASS=0403
PCIDEV=8086:293e
SUBSYS=103c:3629
IRQ=22
HDA=8086:293e
SOFT=8086:293e.HDA
HDAchipVendorID=11c1
CHIP=0x11c11040
IDENT=agrsm
Driver=agrsm

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801I 
      Primary device ID:  8086:293e
    Subsystem PCI_id  103c:3629 
    Softmodem codec or chipset from diagnostics: 0x11c11040
                               from    Archives: 
                        The HDA card softmodem chip is 0x11c11040
      

Support type needed or chipset:    agrsm


Writing DOCs/Intel.txt

The AgereSystems/LSI agrsm code supports compiling of a agrmodem + agrserial driver pair.
There are a few different chipsets which use this driver pair, but they use different code resources:
Chipsets            KV*    PackageNames (most current as of November 2009)
----------------------------------------------------------------------------------------------
11c1:048c and 11c1:048f         2.6.29    agrsm048pci-2.1.60_20091022_i386.deb or agrsm048pci-2.1.60_20091022.tar.gz
11c1:0620                       2.6.28  agrsm06pci_2.1.80~20090825_i386.deb  or agrsm06pci_2.1.80~20090825_i386.tar.gz 
11c11040 (on HDA audio cards)   2.6.31  agrsm-2.6.30.tar.bz2 !!
   All available at: [http://linmodems.technion.ac.il/packages/ltmodem/11c11040/](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/)   , whereat additionally
automation & testing                    agrsm-tools_0.0.1_all.deb or agrsm-tools-0.0.1-2.noarch.rpm
General background                      agrsm_howto.txt 
for rpm variants of dkms-agrsm , see  [http://linux.zsolttech.com/linmodem/agrsm/](http://linux.zsolttech.com/linmodem/agrsm/)
------------------------------------------------------------------------------------------------
* KV == latest kernel release with a reported success 
!! Latest update with major credit to  Nikolay Zhuravlev
Report from  Bjorn Wielens:
Please note- trying to load the modules on a OpenSuSE 11.2 system gives
 an error about the module_version symbol. Using:
# modprobe --force agrmodem
# modprobe --force agrserial 
is necessary to load the drivers, and does not appear to cause ill effects.


All of the above packages are dkms competent.  This means that if your Linux distros dkms package
is previously installed, if provides for future updates matching forthcoming kernels.

-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.4.1
             and the compiler used in kernel assembly: 4.4.1


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.4
   linuc_headers base folder /lib/modules/2.6.31-16-generic/build

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


Checking pppd properties:
    -rwsr-xr-- 1 root dip 277352 2009-02-20 19:25 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
    $ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
    sudo chmod a+x /usr/sbin/pppd

Checking settings of:    /etc/ppp/options
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

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 wlan0 wmaster0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

