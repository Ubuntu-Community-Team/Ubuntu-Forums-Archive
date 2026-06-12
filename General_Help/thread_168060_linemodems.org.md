---
title: "linemodems.org"
date: 2006-04-29
forum: General Help
---

### Post by KRP on 2006-04-29
Hello all. I'm trying to send my modam.data report to the linemodems.org discussion list to see if someone can help me with the report but the mail keeps getting sent back to me un-delivered. Just wondering if anyone could tell me what I'm doing wrong here. Thanks

---

### Post by towsonu2003 on 2006-04-29
I'm not sure why that would happen. What is the reason it gets back to you (do you get an error message inside the returned email)? 

anyway, post your modemdata.txt here and in the meantime, have a look at ubuntu wiki (second link in my signature). 

Hoepfully, your modemdata is easy enough to "decipher" ;)

---

### Post by KRP on 2006-04-29
Thanks for the reply. Here is my modemdata.txt. Thanks for the help.


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, 
Welcome to SUSE LINUX 10.0 (i586) - Kernel  kernel 2.6.13-15-default
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2006_Jan_28
------------ --------------  System information ------------------------
 
Welcome to SUSE LINUX 10.0 (i586) - Kernel 
 on System with processor: i686
 currently under kernel:   2.6.13-15-default
 USB modem not detected.


 The kernel was assembled with compiler:  4.0.2
 a gcc-4.0.2  package must be installed to support driver compiling
Checking for kernel-headers needed for compiling.
Kernel-header resources needed for compiling are not manifestly ready!
Modem candidates are at PCI_buses:  00:1f.6
    
Providing detail for device at  00:1f.6
  with vendor-ID:device-ID
	    ----:----
Class 0703: 8086:24c6   Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
  SubSystem 1179:0001  Toshiba America Info Systems: Unknown device 0001
	Flags: medium devsel, IRQ 11
 Checking for IRQ 11 sharing with modem.
      XT-PIC  uhci_hcd:usb2, ehci_hcd:usb3, Intel 82801DB-ICH4, yenta, eth0

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:24c6 1179:0001 SuSE 2.6.13-15-default  4.0.2 none    i686
      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==

 Vendor=8086 is Intel, Inc. producing HaM and 536ep host controller free (HCF) modems, 537 soft modem
[http://developer.intel.com/design/modems/](http://developer.intel.com/design/modems/) .  Also produced are
AC97 and MC97 controllers managing a varierty of non-Intel soft modem Subsystems.
 These subSystems often have PCI_IDs assigned by the modem assembler, rather than the chip provider.
 Download Intel-537ep drivers through:  [http://developer.intel.com/design/modems/support/drivers.htm](http://developer.intel.com/design/modems/support/drivers.htm)  
 Also check at: [http://linmodems.technion.ac.il/packages/Intel/537/](http://linmodems.technion.ac.il/packages/Intel/537/)  
 for beta releases and perhaps Already compiled drivers for some Linux distributions
 A very detailed installation report cogent to 537 type modems is at:
                  [http://linmodems.technion.ac.il/archive-fifth/msg00541.html](http://linmodems.technion.ac.il/archive-fifth/msg00541.html)

 Setup call id with:
 	Type 1 : When the phone line is not in use                    at+vcid=1
	Type 2 : When the phone line is already in use on a call      at+pcw=0
 ---------------------

  ======= PCI_ID checking completed ====== 
 Update=2006_Jan_28

Analyzing information for PCMCIA device at PCI Bus 01:0b.0
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
	Subsystem: Toshiba America Info Systems: Unknown device 0001
	Flags: bus master, slow devsel, latency 168, IRQ 11
GREPping for an inserted PCMCIA modem with filter:        ommunication
 If a PCMCIA modem is currently inserted and the sockets activated by
    /etc/init.d/pcmcia start
 then the PCMCIA bridge is NOT transparent.

 If the modem is known to have a Lucent digital signal processing chipset,
 then PCMCIA.tar.gz variant assembled by Joern Wustenfeld is necessary,
 rather than the standard ltmodem-8.31a10.tar.gz at  [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
drwxr-xr-x  2 root root 540 2006-04-09 15:18 /dev/.udevdb

There is an active UDEV file system, creating device nodes in volatile RAM.
For SmartLink modems using the slamr.ko or slusb.ko drivers an /etc/init.d/ script
will be necessary to create /dev/slamr0 or /dev/slusb0 ports, or manually by:
#  mknod -m 600 /dev/slamr0 c 242 0
#  mknod -m 600 /dev/slusb0 c 243 0
upon each bootup.

For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant modems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for Lucent/Agere DSP modems
   
 Checking for modem symbolic link support lines within /etc/udev/ files


 The kernel-2.6.13-15-default was compiled with CONFIG_REGPARM, providing more compact and faster code.


      
 The Major.Minor versions differ in the designated compiler none and the 4.0.2 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See [http://linmodems.technion.ac.il/archive-fifth/msg04252.html](http://linmodems.technion.ac.il/archive-fifth/msg04252.html) 
 
Kernel-header resources needed for compiling are not manifestly ready!
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.13-15-default    	[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) or install CD
 Ubuntu 		linux-headers-2.6.13-15-default		[http://http://packages.ubuntu.com/](http://http://packages.ubuntu.com/) or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.13-15-default	   If not present on install CDs search
 	[http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/) 
	[http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE		kernel-source-2.6.13-15-default		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.13-15-default or kernel-smp-devel-2.6.13-15-default on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.13-15-default proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

 A /dev/modem symbolic link is not set.

The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.conf:# ppp over ethernet
/etc/modprobe.conf:# the kernel 2.2 uses pppox
/etc/modprobe.conf:# the kernel 2.4 uses pppoe
/etc/modprobe.conf:alias char-major-108      ppp_generic
/etc/modprobe.conf:alias char-major-144      pppoe
/etc/modprobe.conf:alias net-pf-24           pppoe
/etc/modprobe.conf:# the kernel 2.2 uses ppp.o as ppp driver,
/etc/modprobe.conf:# the kernel 2.4 uses ppp_generic.o
/etc/modprobe.conf:alias ppp0                ppp_generic
/etc/modprobe.conf:alias ppp1                ppp_generic
/etc/modprobe.conf:alias tty-ldisc-3         ppp_async
/etc/modprobe.conf:alias ppp-compress-18          ppp_mppe
/etc/modprobe.conf:alias ppp-compress-21          bsd_comp
/etc/modprobe.conf:alias ppp-compress-24          ppp_deflate
/etc/modprobe.conf:alias ppp-compress-26          ppp_deflate
-------------------------------------
 Resident PPP support modules are properly uncompressed .
----active COMM services are ------------
eth0      Link encap:Ethernet  HWaddr 00:08:0D:5C:E2:CA  
          inet6 addr: fe80::208:dff:fe5c:e2ca/64 Scope:Link
This COMM mode should be closed before using the modem, or DNS services may fail.
 Be sure to read the Ethernet section of Modem/YourModem.txt 
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
ACPI: local apic disabled
apm: BIOS not found.
audit: initializing netlink socket (disabled)
ACPI: PCI interrupt for device 0000:00:1f.6 disabled
pnp: Device 00:08 disabled.
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
toshiba_acpi: Toshiba Laptop ACPI Extras version 0.18
toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
acpi-cpufreq: CPU0 - ACPI performance management activated.

  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the [http://www.smlink.com](http://www.smlink.com)  slmodem software.
  Check pppd version with:
    pppd --version
  See  [http://linmodems.technion.ac.il/archive-fourth/msg03167.html](http://linmodems.technion.ac.il/archive-fourth/msg03167.html)
    

 The following packages should be installed to support compiling and modem testing:
  make, glibc-devel, gcc-3.3 , libasound2-dev, wvdial and kernel-source-2.6.13-15-default 
  SuSE 9.0 and later has pre-compiled drivers supporting the following modem chipsets:
     Intel HaM and 536ep
     Conexant HSF (but not the HCF)
     Lucent/AgereSystems ltmodem (Digital Siggnal Processing type)
     IBM wmave
     Smart Link soft modems
  Unfortunately only the  Intel HaM and 536ep are on the  3 CD Personal set, pending an update.
  Locations on the 6 CD Professional set are:
     CD4/suse/i586/smartlink-softmodem-2.7.9-89.i586.rpm  - the slmodemd daemon
     CD3/suse/i586/km_smartlink-softmodem-2.7.9-89.i586.rpm - slmodem driver compiling
     CD4/suse/i586/hsfmodem-5.03.27mbsibeta02122600-92.i586.rpm - softmodem configuration
     CD4/suse/i586/km_hsfmodem-5.03.27mbsibeta02122600-92.i586.rpm -softmodem driver code
        installation report -  [http://linmodems.technion.ac.il/archive-fourth/msg00350.html](http://linmodems.technion.ac.il/archive-fourth/msg00350.html)
     CD4/suse/i586/ltmodem-8.26a-54.i586.rpm - a patch from SuSE may be needed for function
        installation report - [http://linmodems.technion.ac.il/archive-fourth/msg00458.html](http://linmodems.technion.ac.il/archive-fourth/msg00458.html)
     CD4/suse/i586/Intel-536ep-4.51-200.i586.rpm
     CD4/suse/i586/Intel-v92ham-4.51-244.i586.rpm
     CD4/suse/i586/mwavem-1.0.4-110.i586.rpm
Some pre-compiled SuSE 9.0 packages for the 2.4.21-99-default kernel are available at:
      [http://linmodems.technion.ac.il/packages/SuSE-9.0/](http://linmodems.technion.ac.il/packages/SuSE-9.0/)
  including AgereSoftModem and the Intel537 modems

  IMPORTANT - The kernel-source-144/README.SuSE informs that the pre-assembled kernel-headers installed
  from the 9.0 kernel-source-99 have some flaws.  Upgrading to a later kernel, such as 2.4.21-144 with matching kernel-source is the simplest may of avoiding problems.
  
  SuSE 9.1 comes with a SmartLink slamr.ko driver installed,
  aiding identification of softmodem codecs by:
    dmesg | grep slamr
 
  For the 9.1 Personal (single CD installation) winmodem packages
  have be downloaded from the SuSE 9.1 repository
  Should compiling drivers may be necessary,  the following additional packages
  will have to be downloaded and installed:
  	make, glibc-devel, gcc-3.3.3 and kernel-source.
  The kernel-headers are co-installed with the kernel-source.
  Thus subsequent driver compiling does Not require additional preparations.

---

### Post by towsonu2003 on 2006-04-29
Unfortunately, it isn't very decypherable... especially because it says:
> 
Information on several modem chipset providers is provided below,
because ambiguities remain on the correct choice of supporting software.

It seems you will need to try a couple of drivers, if no help is given by linmodems.org. What's the error message to the emails you send to [email]discuss@linmodems.org[/email]

if you cannot get to email them the modemdata.txt, try referring to the second link in my signature. in there, read and do the following section: 
"Install required Ubuntu packages" where it says: 
**use below quote to locate the section**
> 
    *

      Here, ARCH is your kernel flavour, which you can find out by running $ uname -r, which should give you something like VERSION-XX-ARCH (where ARCH is your kernel flavor, e.g. 386, 686, 686-smp, k7 or k7-smp if you use Intel, powerpc for PPC ...).

      Ubuntu 4.10 and 5.04

      You will need to install the build-essential and linux-headers-ARCH packages. Both of these are on the install CD. One way to install these two packages is to type the following in a terminal (Applications->System Tools->Terminal):

        $ sudo apt-get install build-essential linux-headers-386

      You may be prompted for a password; if so, enter your user password.

      See SynapticHowto and AptGetHowTo for more on installing packages.

      Ubuntu 5.10

      The procedure for 5.10 is similar; unfortunately, some packages necessary for installing the modem driver are not on the Ubuntu 5.10 install CD.

      First, install the build-essential and linux-headers-ARCH packages, as for Ubuntu 4.10 and 5.04 (to get a terminal, use Application->Accessories->Terminal):

       sudo apt-get install build-essential linux-headers-386

      Now, you need also need to install the gcc-3.4 package. If you can connect to the Internet while running 5.10, and have setup your repositories, or perhaps if you have an Ubuntu 5.10 DVD, this is as simple as

       sudo apt-get install gcc-3.4

      It is more likely that you cannot connect to the Internet running Breezy: why would you need a modem driver otherwise? In this case, you will need to download the 3 files listed below on a system which is connected to the Internet, and you'll need to somehow make the files available to your 5.10 system (e.g., write the files to a CD or memory stick, or use a shared hard-drive partition).

      The files are the Ubuntu package files for gcc-3.4-base, cpp-3.4 and gcc-3.4. The appropriate files, at the time of writing, can be found here:
          o

            [WWW] [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb)
          o

            [WWW] [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb)
          o

            [WWW] [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb)

      Assuming you have downloaded the files, and know where they are, you can install them using dpkg:

       sudo dpkg -i gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
       sudo dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb
       sudo dpkg -i gcc-3.4_3.4.4-6ubuntu8_i386.deb

      The order is important.


Also read and try drivers from the following sections:
1.1.6 (installing 536ep)
and 
[http://linmodems.technion.ac.il/archive-fifth/msg00541.html](http://linmodems.technion.ac.il/archive-fifth/msg00541.html)
than this section:
2.4 (wvdial)

if that doesn't work, try this section next: 
1.1.5
and than
2.4 (wvdial)

make sure you deactivate eth0 and any other network interface (card) you may have activated. check them with System>Administration>Networking to "deactivate". 

I would try to send the email to linmodems.org again, as above is longer than a usual winmodem configuration, especially expecting to have errors in every step. 

anyway, if you get errors, copy paste your command and its error, hopig someone will know what it is. good luck ;)

---

### Post by KRP on 2006-04-29
towsonu2003, thanks for the help. Here is the error message I get when I try the email. I'm just copying and pasting the text into the email.



Hi. This is the qmail-send program at ns0.crynwr.com.
I'm afraid I wasn't able to deliver your message to the following addresses.
This is a permanent error; I've given up. Sorry it didn't work out.

<discuss@linmodems.org>:
ezmlm-reject: fatal: Sorry, I don't accept messages of MIME Content-Type 'multipart/alternative' (#5.2.3)

---

### Post by towsonu2003 on 2006-04-29
[QUOTE=KRP]
ezmlm-reject: fatal: Sorry, I don't accept messages of MIME Content-Type 'multipart/alternative' (#5.2.3)[/QUOTE]
I believe they only accept text-emails. So if you are using outlook, you'll have to tell it to use text-formatting (or similar) in options (I think??). yahoo has such an option as well. I think google has that by default, but not sure. 

basically, you have to tell the system you are using to send this message as a text (no html, nothing).

---

