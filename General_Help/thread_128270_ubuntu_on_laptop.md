---
title: "ubuntu on laptop"
date: 2006-02-11
forum: General Help
---

### Post by screener on 2006-02-11
i'm new to ubuntu and a newbe to linux . . . i think it's great 

i just have some problems with it concerning the modem and the bluetooth 

my WIFI is working codecs every thing is good 

i dont know how to but a driver for the modem (and what is the modem) ?? it's a laptop i use it out doors so i need to dail out  

my computer is a acer extensa 6601WLMi
intel pentium M processor 725
(1.6 GHz, 400 MHz FSB, 2 MB L2 cache)
512MB DDR2

can someone help me do this coz i would realy love to have it as my main OS 



Thanx 

Screener

---

### Post by screener on 2006-02-11
Oh and i have used [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu) to add software to the OS 


and sorry one more thing the battery life and how long do i have left is not coming up ??  how can i make it work ?

Thanx again 


Screener

---

### Post by briguy on 2006-02-11
You should be able to add a battery monitor to the panel if it's not already there.  Just right click on the panel, select add applet then the battery monitor.  You can configure that with a right click again.

You might have trouble with the modem, google linmodem to learn more if you're really interested.

I've never used bluetooth under linux, and without any more information from you I can't help! :)

I've switched completely to Ubuntu for just over a year now - you won't regret it!

---

### Post by drakeoutlaw on 2006-02-11
Go to [http://linmodems.org](http://linmodems.org)

Here you will learn how to:
1. Identify your modem chipset with scanModem tool
2. Download driver
3. Compile or Install driver
4. Make/set connection parameters (user, password ph no. etc.) using pppconfig or wvdial. 

Or chuck all that, buy an external or pcmcia linux compatible modem.  See [http://start.at/modem](http://start.at/modem)

---

### Post by screener on 2006-02-11
i will look into linmodem 

and will let u know :) 

but for the bluetooth it was working with suse 10 and it was super nice

---

### Post by screener on 2006-02-11
i did the scan for the modem and  . . . . nothing . . . i dont understand anything

when i did the scan this is what i got on the terminal

> UPDATE=2006_Jan_28
ONLY use scanModem downloaded as: [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

./scanModem should ONLY be run within a Linux/UNIX partition.
If within a MicroSoft/DOS partition, abort with Ctrl-C now !!!
Copy scanModem.gz to your Linux partition and restart.

PCIBUS=0000:00:1e.3

Providing detail for device at  0000:00:1e.3
  with vendor-ID:device-ID
            ----:----
Class 0703: 8086:266d   Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04) (prog-if 00 [Generic])
  SubSystem 1025:0066  Acer Incorporated [ALI]: Unknown device 0066
        Flags: medium devsel, IRQ 10

                  -----PCI_IDs-------                    --CompilerVer-
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:266d 1025:0066 ubuntu 2.6.12-10-386  3.4.5 4.0.2    i686
              From records, 1025:0066 has soft modem codec type CXT
 The hsfmodem drivers from [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers) are the ONLY support of ConeXanT codec modems under Linux!!


 The controller: 8086:266d 82801EB ICH6
 is capable of supporting soft modem chips from AT LEAST manufacturers:
        Conexant
        Smartlink



and in the modem folder that was made 

i found 4 txt files


the modemData.txt  with this in it 

> 

 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-10-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2006_Jan_28
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-10-386
 USB modem not detected.


 The kernel was assembled with compiler:  3.4.5
 with current System compiler GCC=4.0.2
Checking for kernel-headers needed for compiling.
Kernel-header resources needed for compiling are not manifestly ready!
Modem candidates are at PCI_buses:  0000:00:1e.3
    
Providing detail for device at  0000:00:1e.3
  with vendor-ID:device-ID
	    ----:----
Class 0703: 8086:266d   Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04) (prog-if 00 [Generic])
  SubSystem 1025:0066  Acer Incorporated [ALI]: Unknown device 0066
	Flags: medium devsel, IRQ 10
 Checking for IRQ 10 sharing with modem.
      XT-PIC  uhci_hcd:usb3, uhci_hcd:usb4, yenta, i915@pci:0000:00:02.0

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:266d 1025:0066 ubuntu 2.6.12-10-386  3.4.5 4.0.2    i686
 ALSA modem drivers of kernel-version 2.6.8 and earlier lack support for the 8086:266d soft modem controller
              From records, 1025:0066 has soft modem codec type CXT
 The hsfmodem drivers from [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers) are the ONLY support of ConeXanT codec modems under Linux!!

       
 The controller: 8086:266d 82801EB ICH6
 is capable of supporting soft modem chips from AT LEAST manufacturers:
	Conexant
	Smartlink
 The Subsystem PCI id does not itself identify the modem Codec.
Checking for autoloaded ALSA modem drivers



in the softmodem.txt . . . i got this 

>     
                  Soft Modem Information

The earlier generations of modems had chips with digital signal processing (DSP) capability in which
most of the total modem effort proceeded.  The "soft modem" is a generic name for modems 
which lack DSP.  Rather, the CPU does almost all the signal processing as directed by software code. 
There are a few soft modems which are fully identified by the primary PCI ID of the modem card, 
such as the Agere Systems 11c1:048(a,b,c,d) series.

The larger family is more troublesome, for identification of supporting software. 
They are comprised of a primary modem controller which can host a variety of Subsystems. 
Both the primary PCI ID and "mc97 codec"  written in a Subsystem firmware chip are required,
for assessing support under Linux.  Only subsequently is the Subsystem PCI ID useful, for record keeping.  

The scanModem script contains five routines for acquiring  the critical mc97 codec identification:
1) a modem driver independent test, only usefull for some of the earliest soft modems,
   described at the end of this file;
2) a test using modem drivers already on your System,  as part of  the ALSA (Advanced Linux Sound
 Architecture) software package ; See Slmodem-ALSA.txt for details.
3) a test requiring the SmartLink slamr.ko driver:  see Slmodem.txt ;
4) comparison with PCI IDs with codecs historically gathered and stored within scanModem;
5) In case 1-4 are not adequate, there are the following instructions for running ATI queries under Microsoft windows.
Chipset information may be obtained under Microsoft Windows through:
 1) Start > Settings > Control Panel > Classical View (for WinXP) > System > Hardware > 
   DeviceManager > Modems  > Click on the +  > Modem  
   Double click to expand the graphic.  Manufacturer information may be displayed.  For example, 
   CXT stands for Conexant.  
   Click the Diagnostics Tab,  Record any Hardware ID  or Vendor & Device information.
   Next do the Query Modem and record the ATI specifications. 
   Try to identify the modem setup file, with name perhaps MODEM.INF
 2) Open a COMM console, and send ATI commands to the modem (ATI, ATI1, ATI2, etc)
   which may elicit chipset and driver information. Here is an example
       ATI3 - Agere SoftModem Version 2.1.22
       ATI5 - 2.1.22, AMR Intel MB, AC97 ID:SIL REV:0x27
   successfully identifying an Agere SoftModem chipset, both by name and through
   the:softmodem SIL ID:              AC97 ID:SIL REV:0x27
 
 The IBM mwave modem is not a softmodem, but  cannot be detected by scanModem.  
 But the mwave driver is included in 2.6.n kernel releases.  So try
 #  modprobe mwave
 Either the module will load, or the absence of the modem will be indicated by:
FATAL: Error inserting mwave (/lib/modules/2.6.10-1-686/kernel/drivers/char/mwave/mwave.ko): Input/output error
See [http://www.linuxdocs.org/HOWTOs/mini/ACP-Modem/](http://www.linuxdocs.org/HOWTOs/mini/ACP-Modem/)  for details on this modem.

Subsystems for softmodems are primarily made by Silicon Labs (SIL), 
under contract to companies like Intel, Agere Systems, Motorola  etc.
In the Table below,
The ChipMadeBy does NOT imply software support directly from that manufacturer.

The chart of information below is largely harvested from messages to [email]discuss@linmodems.org[/email].
 A codec_indent  like REV:0x27 is reported by diagnostics under Microsoft, as illustrated above. 
The matching designation like SIL27 are translations under Linux, 
    output by a diagnostic of the slamr.ko driver, from the SmartLink slmodem software. 
The SIL is an abbreviation for  Silicon Laboratorys Inc., which provides Subsystems for many total modem assemblies. 
SML is used below as abbreviation for SmartLink Inc.,  with official driver resources at
       [http://www.smlink.com/main/index1.php?ln=en&main_id=40](http://www.smlink.com/main/index1.php?ln=en&main_id=40)  and recent patches provided at:
       [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 

   codec_ident    ID translation     driver sources 
---------------------  ------------------      -------------------------       
 0x21      SIL21   PCTel     for 2.4.n kernels, pctel-2.7.9 at [http://linmodems.technion.ac.il/pctel-linux](http://linmodems.technion.ac.il/pctel-linux),
                                             and SML for  2.4.n or 2.6.n kernels
 0x23      SIL23   PCtel      same as SIL21               
 0x22      SIL22   SML
 0x26      SIL26   SML              
 0x24      SIL24   Broadcom, use   SML drivers
 ????      BCM64  Broadcom, use   SML in ALSA mode,  but only under the Intel ICH modem controllers.
0x25      SIL25   Intel 537AA		"  or SML
????        INT65   Intel 537EA	[http://linmodems.technion.ac.il/packages/Intel/537/](http://linmodems.technion.ac.il/packages/Intel/537/) or SML
0x27      SIL27   AgereSystems(AS), use  SML  needed under 2.6.n kernels,
                             but for  2.4.n, there are also AS drivers through  [http://www-3.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-52698](http://www-3.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-52698)  
0x2F      SIL2F     Same as SIL27
 ????       CXT(21,22,23,29,41  and others)   Conexant -   	[http://www.linuxant.com/drivers](http://www.linuxant.com/drivers), the hsfmodem package      
 -------------------------------------------------------------------------------- 
  If a novel identifier is displayed during diagnostics, please report to [email]discuss@linmodems.org[/email]
 
A rough/practical guide is first given, with some qualifications and exceptions to follow:
     SILnm  (n,m digits) are SML supportable;
     CXTnm are ONLY supported by the  [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers), the hsfmodem package ;
     INTnm  are supported by Intel drivers and perhaps slmodemd with ALSA support;
     BCMnm, INT65  (and similar name styles) have had successes with SmartLink slmodem in ALSA mode.
     See the companion Slmodem-ALSA.txt for details.
Qualifications  to the Table below relate to Linux software support for soft modem controllers.
In particular,  no software package provides support for all soft modem controllers.
    	     
Primary              
PCI_IDs           Name	                   Possible support by:
---------------  -----------------------------  -------------------------
8086:1080 ac97 controller 				i . 
8086:2416 82801AA ICHAA >  		+ A a  p c .
8086:2426 82801AB ICHAB > 		+ A a .
8086:7186 >				        			c .
8086:7196 82440 Banister  >     	+ A a      c .
8086:2446 82801BA ICH2  > 		+ A a p c .
8086:2486 82801CA/CAM ICH3 > 	+ A a p c i .
8086:82801DB ICH4 > 		+ A a   c i b .
8086:24d6 82801EB ICH5 > 		+ A     c i .
8086:266d 82801EB ICH6> 	        + A	c .
8086:2668 Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller> A c .
8086:xxxx types above are from Intel   

1039:7013  SIS 630 >               		+ a p c i .
1039:7018  SIS 960 >               		+       i .
10de:01c1  Nvidia Corp >          		+       i .
10de:00d9  Nvidia Corp >			    A      c   .
1106:3068  VIA >			+ a p c i .
1022:7446  AMD AC_LINK >		+ .
10b9:5450  ALI 5450 >
10b9:5451  ALI 5451 >			+ a .
10b9:5453  ALI 5453 AC-Link  >	      	p c .
1025:5453  ALI 5453 AC-Link  > 		    c .
10b9:5457  ALI 5457 AC-Link > 	+    p   c i .
1025:5457  ALI 5457 AC-Link  >        	     c .                   .
e159:0001  TigerJet >			          		i .
1002:434d  ATI >					  T  a    c i .
1002:4378 ATI >						     c .
1543:3052  SI3052 >                               		i .
  --------------------------------------------------------
The following letters indicate compatibility for the modem controller,
BUT do NOT gaurantee support by the software. 
Support MUST be ascertained by identifing the soft modem codec.

  +   SmartLink (SML) - [http://www.smlink.com](http://www.smlink.com),  the slmodem-2.n.m series
  A   SML slmodem-2.n.m-alsa software supporting the ALSA intel8x0m-modem driver
      Soft modems with the Broadcom codec BCM64 should thus be served. 
  T   SML slmodem-2.n.m-alsa software supporting the ALSA snd-atiixp-modem driver
With the above SML software, port creation is controlled by a daemon, slmodemd,
rather than being a static feature of the /dev/ files.
  a   AgereSystems only under 2.4.n
  p   PCtel support at [http://pctelcompdb.sourceforge.net/](http://pctelcompdb.sourceforge.net/)
  c   Conexant/Rockwell - [http://www.linuxant.com](http://www.linuxant.com)
  i   Intel - [http://www.intel.com](http://www.intel.com)
  b   Broadcom, under 2.4.n kernels, with ALSA code under 2.6.n
  for details on A and T slmodem implementations, see Modem/Slmodem-ALSA.txt
 ===========================================================

To achieve codec readouts for SmartLink (SML) compatible modem controllers listed above,
follow the directions in Slmodem.txt.

The 1) driver independent test, some details
During bootup, kernel diagnostics on the System are stored for later display by:
 	dmesg
This information may include a SIL_id of modems under AC97/MC97 Controllers,
depending upon the type of bridging of the modem card to the motherboard.
The scanModem script processes dmesg output to capture AC97 modem information,
parses it into a SIL_id if possible, and then displays of modem chipset information.
Guidance to sources of modem supporting software may thus be obtained.

The transfer of the AC97 information to the dmesg buffer requires that modules supporting
both the digital audio card and the ac97_codec be loaded during bootup:
    modprobe ac97_codec
    modprobe audio_drivers  (such as i810_audio)
This can be checked after bootup with:
   lsmod

This script can also be used by entering a test block with nomenclature:
        ./scanModem SILtest
with SILtest a text file in This Folder
containing a section of a dmesg output or /var/log/messages like:

  i810: Intel ICH 82801AA found at IO 0xdc00 and 0xd800, IRQ 11
  i810_audio: Audio Controller supports 2 channels.
  ac97_codec: AC97 Audio codec, id: 0x4144:0x5340 (Analog Devices AD1881)
  i810_audio: AC97 codec 0 Unable to map surround DAC's (or DAC's not present), total channels = 2
  ac97_codec: AC97 Modem codec, id: 0x5349:0x4c22 (Silicon Laboratory Si3036)

which does include a line beginning with:   ac97_codec: AC97 Modem codec, id:
 


in the UNSUBSCRIBE.txt

>    For instructions to UNSUBSCRIBE from [email]discuss@linmodems.org[/email],
   send an email to:   [email]discuss-help@linmodems.org[/email]



and in the yourModem.txt 

NOTHING !

it was clean 



please help

thanx

---

### Post by screener on 2006-02-16
i found the modem driver at linuxant.com withooth  the help of limodems.org
it works !! yes it works 

but i have the problem of the bluetooth ??
i could not get it to work . . . i have tryed playing around with it but nothing 

waiting for some one to help 

Thanx

---

### Post by screener on 2006-02-20
still waiting for someone to help!!


thanx


Screener

---

