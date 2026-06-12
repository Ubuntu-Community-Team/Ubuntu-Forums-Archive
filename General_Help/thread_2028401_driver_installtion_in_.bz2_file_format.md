---
title: "driver installtion in .bz2 file format"
date: 2012-07-18
forum: General Help
---

### Post by fatboy07 on 2012-07-18
Hello Guys, can somebady help me how to install my usb wifi, I find that the driver is in .bz2 file. Thanks in advance!

---

### Post by MG&amp;TL on 2012-07-18
Okay, what's the driver? There may be an easier way, this looks like a compile-from-source job.

Anyway, unzip the file and tell us what's in the folder it extracted to.

---

### Post by fatboy07 on 2012-07-18
[IMG]http://s18.postimage.org/oaoq9dfvd/extracted.jpg[/IMG]
this is the files after extraction. Thanks

---

### Post by MG&amp;TL on 2012-07-18
Okay, what's in the README_STA_usb file? Post in [QUOTE] tags or something to differentiate it.

---

### Post by fatboy07 on 2012-07-18
> * README
*
* Ralink Tech Inc.
* 
* [http://www.ralinktech.com](http://www.ralinktech.com)
*

=======================================================================
ModelName:
===========
RT2870 Wireless Lan Linux Driver


=======================================================================
Driver lName:
===========
rt2870.o/rt2870.ko


=======================================================================
Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.


=======================================================================
Ralink Hardware:
===================
Ralink 802.11n Wireless LAN Card.


=======================================================================
Description:
=============
This is a linux device driver for Ralink RT2870 USB ABGN WLAN Card.


=======================================================================
Contents:
=============
Makefile	        : Makefile
*.c					: c files
*.h					: header files


=======================================================================
Features:
==========
   This driver implements basic IEEE802.11. Infrastructure and adhoc mode with 
   open or shared or WPA-PSK or WPA2-PSK authentication method. 
   NONE, WEP, TKIP and AES encryption. 


=======================================================================
Build Instructions:  
====================

1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   => #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make
	# compile driver source code
	# To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2870sta
	
=======================================================================
CONFIGURATION:  
====================
RT2870 driver can be configured via following interfaces, 
i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file

i)  iwconfig comes with kernel.  
ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.
iii)modify configuration file "RT2870STA.dat" in /etc/Wireless/RT2870STA/RT2870STA.dat.
           
Configuration File : RT2870STA.dat
---------------------------------------
# Copy this file to /etc/Wireless/RT2870STA/RT2870STA.dat
# This file is a binary file and will be read on loading rt.o module.
#
# Use "vi RT2870STA.dat" to modify settings according to your need.
# 
# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure
# 2.) set Channel to "0" for auto-select on Infrastructure mode
# 3.) set SSID for connecting to your Accss-point.
# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"
# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"
# for more information refer to the Readme file.
# 
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
SSID=Dennis2860AP
NetworkType=Infra
WirelessMode=9
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
WmmCapable=0
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
FastRoaming=0
RoamThreshold=70
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=
CarrierDetect=0

-----------------------------------------------
*NOTE:
	WMM parameters
			WmmCapable			Set it as 1 to turn on WMM Qos support				
			AckPolicy1~4		Ack policy which support normal Ack or no Ack
								(AC_BK, AC_BE, AC_VI, AC_VO)		
	
	All WMM parameters do not support iwpriv command but ¡¥WmmCapable¡&#352;¡&#352;, 
	please store all parameter to RT2870STA.dat, and restart driver. 	

-----------------------------------------------
syntax is 'Param'='Value' and describes below. 

@> CountryRegion=value                                 
	value
		0: use 1 ~ 11 Channel
		1: use 1 ~ 13 Channel
		2: use 10 ~ 11 Channel
		3: use 10 ~ 13 Channel
		4: use 14 Channel
		5: use 1 ~ 14 Channel
		6: use 3 ~ 9 Channel
		7: use 5 ~ 13 Channel
	   31: use 1 ~ 14 Channel (ch1-11:active scan, ch12-14 passive scan)
   	 	                                      
@> CountryRegionABand=value      							
	value	
		0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel
		1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel
		2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel
		3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel
		4: use 149, 153, 157, 161, 165 Channel
		5: use 149, 153, 157, 161 Channel
		6: use 36, 40, 44, 48 Channel
		7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel
		8: use 52, 56, 60, 64 Channel
		9: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 132, 136, 140, 149, 153, 157, 161, 165 Channel
	   10: use 36, 40, 44, 48, 149, 153, 157, 161, 165 Channel
	   11: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 149, 153, 157, 161 Channel

@> CountryCode=value
	value
		AG, AR, AW, AU, AT, BS, BB, BM, BR, BE, BG, CA, KY, CL, CN, CO, CR, CY, CZ, DK, DO, EC, SV, FI, FR, DE, 
		GR, GU, GT, HT, HN, HK, HU, IS, IN, ID, IE, IL, IT, JP, JO, LV, LI, LT, LU, MY, MT, MA, MX, NL, NZ, NO,
		PE, PT, PL, RO, RU, SA, CS, SG, SK, SI, ZA, KR, ES, SE, CH, TW, TR, GB, UA, AE, US, VE
		"" => using default setting: 2.4 G - ch 1~11; 5G - ch 52~64, 100~140, 149~165
                                                           
@> SSID=value                	
	value
		0~z, 1~32 ascii characters.
                    	
@> WirelessMode=value
	value	
		0: legacy 11b/g mixed 
		1: legacy 11B only 
		2: legacy 11A only         //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
		3: legacy 11a/b/g mixed     //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
		4: legacy 11G only
		5: 11ABGN mixed
		6: 11N only
		7: 11GN mixed
		8: 11AN mixed
		9: 11BGN mixed
	   10: 11AGN mixed	
                     
@> Channel=value
	value
		depends on CountryRegion or CountryRegionABand
                    	
@> BGProtection=value
	value
		0: Auto 
		1: Always on 
		2: Always off
                    	
@> TxPreamble=value
  	value
		0:Preamble Long
		1:Preamble Short 
		2:Auto
                    	
@> RTSThreshold=value
	value
		1~2347                                                       
                    	                                       
@> FragThreshold=value
	value       	
		256~2346
                    	
@> TxBurst=value
	value
		0: Disable
		1: Enable

@> NetworkType=value	    		
	value 
		Infra: infrastructure mode
       	Adhoc: adhoc mode
                                                                                                                                                        	                                                          
@> AuthMode=value
	value
		OPEN	 	For open system	
		SHARED	  	For shared key system	
		WEPAUTO     Auto switch between OPEN and SHARED
		WPAPSK      For WPA pre-shared key  (Infra)
		WPA2PSK     For WPA2 pre-shared key (Infra)
		WPANONE		For WPA pre-shared key  (Adhoc)
		WPA         Use WPA-Supplicant
		WPA2        Use WPA-Supplicant

@> EncrypType=value
	value
		NONE		For AuthMode=OPEN                    
		WEP			For AuthMode=OPEN or AuthMode=SHARED 
		TKIP		For AuthMode=WPAPSK or WPA2PSK                    
		AES			For AuthMode=WPAPSK or WPA2PSK                     
		
@> DefaultKeyID=value
	value
		1~4

@> Key1=value
    Key2=value
    Key3=value
    Key4=value
	value
		10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
    (usage : "iwpriv" only)     

@> Key1Type=vaule
    Key2Type=value
    Key3Type=vaule
    Key4Type=vaule
    value
		0   hexadecimal type
		1   assic type
    (usage : reading profile only)

@> Key1Str=value
    Key2Str=value
    Key3Str=vaule
    Key4Str=vaule
    value
		10 or 26 characters (key type=0)
		5 or 13 characters  (key type=1)
    (usage : reading profile only)	

@> WPAPSK=value              	
	value
		8~63 ASCII  		or 
		64 HEX characters
																                    																		
@> WmmCapable=value
	value
		0: Disable WMM
		1: Enable WMM
        
@> PSMode=value
    value
    	CAM			    Constantly Awake Mode
		Max_PSP		    Max Power Savings
		Fast_PSP		Power Save Mode

@> FastRoaming=value
	value
		0				Disabled
		1				Enabled

@> RoamThreshold=value
	value
		Positive Interger(dBm)

@> HT_RDG=value
	value
		0				Disabled
		1				Enabled

@> HT_EXTCHA=value (Extended Channel Switch Announcement)
	value
		0				Below
		1 				Above

@> HT_OpMode=value
	value
		0				HT mixed format
		1				HT greenfield format

@> HT_MpduDensity=value
	value (based on 802.11n D2.0)
		0: no restriction
		1: 1/4 £gs
		2: 1/2 £gs
		3: 1 £gs
		4: 2 £gs
		5: 4 £gs
		6: 8 £gs
		7: 16 £gs

@> HT_BW=value
	value
		0				20MHz
		1				40MHz

@> HT_AutoBA=value
	value
		0				Disabled
		1				Enabled

@> HT_BADecline
	value
		0				Disabled
		1			    Enabled <Reject BA request from AP>

@> HT_AMSDU=value
	value
		0				Disabled
		1				Enabled

@> HT_BAWinSize=value
	value
		1 ~ 64

@> HT_GI=value
	value
		0				long GI
		1				short GI

@> HT_MCS=value
	value
		0 ~ 15
		33: auto

@> HT_MIMOPSMode=value
	value (based on 802.11n D2.0)
		0				Static SM Power Save Mode
		1				Dynamic SM Power Save Mode
		2				Reserved
		3				SM enabled
	(not fully support yet)

@> EthConvertMode=value
	value
		dongle
		clone
		hybrid

@> EthCloneMac=value
	value
		xx:xx:xx:xx:xx:xx

@> IEEE80211H=value
	value
		0				Disabled
		1				Enabled

@> TGnWifiTest=value
	value
		0				Disabled
		1				Enabled

@> WirelessEvent=value
	value
		0				Disabled
		1				Enabled <send custom wireless event>
	    
@> MeshId=value
	value
		Length 1~32 ascii characters

@> MeshAutoLink=value
	value
		0				Disabled
		1				Enabled

@> MeshAuthMode=value
	value
		OPEN	 	For open system	
		WPANONE		For WPA pre-shared key  (Adhoc)

@> MeshEncrypType=value
	value
		NONE		For MeshAuthMode=OPEN                    
		WEP			For MeshAuthMode=OPEN
		TKIP		For MeshAuthMode=WPANONE
		AES			For MeshAuthMode=WPANONE

@> MeshWPAKEY=value
	value
		8~63 ASCII  		or 
		64 HEX characters

@> MeshDefaultkey=value
	value
		1~4

@> MeshWEPKEY=value
	value
		10 or 26 characters
		5 or 13 characters

@> CarrierDetect=value
	value
		0				Disabled
		1				Enabled

MORE INFORMATION
=================================================================================
If you want for rt2870 driver to auto-load at boot time:
A) choose ra0 for first RT2870 WLAN card, ra1 for second RT2870 WLAN card, etc.
   
B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,      
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2870sta
   
C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0  
   DEVICE='ra0'
   ONBOOT='yes'     


NOTE:
   if you use dhcp, add this line too .
    BOOTPROTO='dhcp'

*D) To ease the Default Gateway setting, 
    add the line
    GATEWAY=x.x.x.x   
    in /etc/sysconfig/network
   
=======================================================================
Dongle/Clone Features:
======================
A) Dongle mode: 
   	Provides a 1-to-N MAC address mapping mechanism such that more than one PC behind the STA 
   	can transparently connect to the AP.

B) Clone mode:
	Provides a 1-to-1 MAC address mapping mechanism. 
	STA can use own MAC as SA MAC or 
			use user desired MAC as SA MAC or
		    use source MAC of first packet coming from wired device as SA MAC.
	NOTE: In this mode, only the PC who own the specified MAC can connect to the AP.

 
C) Hybrid mode(Dongle+Clone):
	Provides a 1-to-N MAC address mapping mechanism such that more than one PC behind the STA 
   	can transparently connect to the AP.
	STA can use own MAC as SA MAC or 
			use user desired MAC as SA MAC or
		    use source MAC of first packet coming from wired device as SA MAC.

D) Please refer to "Config STA to link as dongle mode..." in iwpriv_usage.txt for releated commands.

inside of this file.

---

### Post by MG&amp;TL on 2012-07-18
It might be a better idea to tell us what your hardware is. That looks excessively complicated and is for kernels 2.4 and 2.6. We're on 3.2 now.

Post output of

```
lsusb
```

please. :)

---

### Post by fatboy07 on 2012-07-19
> **MG&TL said:**
> It might be a better idea to tell us what your hardware is. That looks excessively complicated and is for kernels 2.4 and 2.6. We're on 3.2 now.

Post output of

```
lsusb
```

please. :)

Thanks for trying to help me, sorry Im too dumb, How can I tell what is my hardware? I just downloaded the drivers/files from the ralink site.

---

### Post by MG&amp;TL on 2012-07-19
> **fatboy07 said:**
> Thanks for trying to help me, sorry Im too dumb, How can I tell what is my hardware? I just downloaded the drivers/files from the ralink site.

You're not dumb, you just haven't done this before.

Open a terminal and type:

```
lsusb
```

then post the output back here, preferable in [CODE] tags (the # on the top bar thing).

Thanks. :)

---

### Post by 3rdalbum on 2012-07-19
What version of Ubuntu are you on?

Ubuntu 11.10 and later should support your Wifi device out-of-the-box, assuming it's an RT2870 in there. Just plug it in and use the Network Manager applet to choose your network.

Ubuntus 10.04-11.04 have the driver already, but it doesn't work out-of-the-box because of a driver conflict. You need to blacklist the conflicting driver by adding "blacklist rt2800usb" to the /etc/modprobe.d/blacklist.conf file; you can do it via this:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Go to the bottom of the file and on a new line, put the words "blacklist rt2800usb" without the quote marks. Save your changes and reboot.

Of course, if you're using an old version of Ubuntu I'd recommend you update to Ubuntu 12.04, currently the latest version of Ubuntu. This isn't Windows where you can stay on a version for twelve years.

DO NOT install your driver manually until you have tried my suggestion. If you already have a preinstalled driver for your wifi device you'll just make things a little worse for yourself by doing a manual install.

---

### Post by fatboy07 on 2012-07-19
> **MG&TL said:**
> You're not dumb, you just haven't done this before.

Open a terminal and type:

```
lsusb
```

then post the output back here, preferable in ```
 tags (the # on the top bar thing).

Thanks. :)


Thanks a lot, this is what I get.

[CODE]drei@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
drei@ubuntu:~$ 

```

---

### Post by fatboy07 on 2012-07-19
> **3rdalbum said:**
> What version of Ubuntu are you on?

Ubuntu 11.10 and later should support your Wifi device out-of-the-box, assuming it's an RT2870 in there. Just plug it in and use the Network Manager applet to choose your network.

Ubuntus 10.04-11.04 have the driver already, but it doesn't work out-of-the-box because of a driver conflict. You need to blacklist the conflicting driver by adding "blacklist rt2800usb" to the /etc/modprobe.d/blacklist.conf file; you can do it via this:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Go to the bottom of the file and on a new line, put the words "blacklist rt2800usb" without the quote marks. Save your changes and reboot.

Of course, if you're using an old version of Ubuntu I'd recommend you update to Ubuntu 12.04, currently the latest version of Ubuntu. This isn't Windows where you can stay on a version for twelve years.

DO NOT install your driver manually until you have tried my suggestion. If you already have a preinstalled driver for your wifi device you'll just make things a little worse for yourself by doing a manual install.

IM using lubuntu the light weight vesion. :)

---

### Post by MG&amp;TL on 2012-07-19
> **fatboy07 said:**
> IM using lubuntu the light weight vesion. :)

He'd like the number. :)

If you don't know, post the output of 

```
lsb_release -a
```

That doesn't look like a RT2870 to me...

---

### Post by fatboy07 on 2012-07-19
> **MG&TL said:**
> He'd like the number. :)

If you don't know, post the output of 

```
lsb_release -a
```

That doesn't look like a RT2870 to me...

```
drei@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise
drei@ubuntu:~$ 
```

this is what I got. :)

---

### Post by fatboy07 on 2012-07-19
> **MG&TL said:**
> He'd like the number. :)

If you don't know, post the output of 

```
lsb_release -a
```

That doesn't look like a RT2870 to me...

is this what we need? "RT5370 Wireless Adapter"

---

### Post by MG&amp;TL on 2012-07-19
> **fatboy07 said:**
> is this what we need? "RT5370 Wireless Adapter"

Yeah, the others are just empty USB ports, I think.

---

### Post by fatboy07 on 2012-07-19
> **MG&TL said:**
> Yeah, the others are just empty USB ports, I think.

So whats next? :)

---

### Post by MG&amp;TL on 2012-07-19
> **fatboy07 said:**
> So whats next? :)


I don't know. I was kind of hoping 3rdAlbum would turn up again, he seems to be good with drivers. I'll do some googling. :)

This looks a bit like you: [http://ubuntuforums.org/showthread.php?t=1800178](http://ubuntuforums.org/showthread.php?t=1800178)

---

### Post by fatboy07 on 2012-07-19
> **MG&TL said:**
> I don't know. I was kind of hoping 3rdAlbum would turn up again, he seems to be good with drivers. I'll do some googling. :)

This looks a bit like you: [http://ubuntuforums.org/showthread.php?t=1800178](http://ubuntuforums.org/showthread.php?t=1800178)

thanks! but i have tried it and I have error in make. :(

---

### Post by fatboy07 on 2012-07-19
> FATAL: Module rt5370sta not found
 got this error..

---

### Post by MG&amp;TL on 2012-07-19
> **fatboy07 said:**
> got this error..

Okay, was there any error output from the other commands?

---

### Post by fatboy07 on 2012-07-19
> drei@ubuntu:~$ sudo modprobe rt5370sta
[sudo] password for drei: 
FATAL: Module rt5370sta not found.
drei@ubuntu:~$ cdcd Desktop/RT5370
The program 'cdcd' is currently not installed.  You can install it by typing:
sudo apt-get install cdcd
drei@ubuntu:~$ cd Desktop/RT5370
bash: cd: Desktop/RT5370: No such file or directory
drei@ubuntu:~$ cd Desktop/RT5370
bash: cd: Desktop/RT5370: Not a directory
drei@ubuntu:~$ cd Desktop/zach
drei@ubuntu:~/Desktop/zach$ sudo du
28	./tools
532	./os/linux
536	./os
2100	./common
804	./sta
264	./chips
108	./include/os
168	./include/chip
12	./include/iface
1080	./include
4888	.
drei@ubuntu:~/Desktop/zach$ make clean
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/drei/Desktop/zach/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Modules.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/drei/Desktop/zach/os/linux'
rm -rf os/linux/Makefile
drei@ubuntu:~/Desktop/zach$ make
make -C tools
make[1]: Entering directory `/home/drei/Desktop/zach/tools'
gcc -g bin2h.c -o bin2h
make[1]: gcc: Command not found
make[1]: *** [all] Error 127
make[1]: Leaving directory `/home/drei/Desktop/zach/tools'
make: *** [build_tools] Error 2
drei@ubuntu:~/Desktop/zach$ make install
make -C /home/drei/Desktop/zach/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/drei/Desktop/zach/os/linux'
rm -rf /etc/Wireless/RT2870STA
rm: cannot remove `/etc/Wireless/RT2870STA/RT2870STA.dat': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/drei/Desktop/zach/os/linux'
make: *** [install] Error 2
drei@ubuntu:~/Desktop/zach$ sudo su
root@ubuntu:/home/drei/Desktop/zach# make clean
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/drei/Desktop/zach/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Modules.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/drei/Desktop/zach/os/linux'
rm -rf os/linux/Makefile
root@ubuntu:/home/drei/Desktop/zach# make
make -C tools
make[1]: Entering directory `/home/drei/Desktop/zach/tools'
gcc -g bin2h.c -o bin2h
make[1]: gcc: Command not found
make[1]: *** [all] Error 127
make[1]: Leaving directory `/home/drei/Desktop/zach/tools'
make: *** [build_tools] Error 2
root@ubuntu:/home/drei/Desktop/zach# make install
make -C /home/drei/Desktop/zach/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/drei/Desktop/zach/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/drei/Desktop/zach/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/
install: cannot stat `rt5370sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/drei/Desktop/zach/os/linux'
make: *** [install] Error 2
root@ubuntu:/home/drei/Desktop/zach# modeprobe -r rt5370sta
No command 'modeprobe' found, did you mean:
 Command 'modprobe' from package 'module-init-tools' (main)
modeprobe: command not found
root@ubuntu:/home/drei/Desktop/zach# modeprobe rt5370sta
No command 'modeprobe' found, did you mean:
 Command 'modprobe' from package 'module-init-tools' (main)
modeprobe: command not found
root@ubuntu:/home/drei/Desktop/zach# 


this is what I got..

---

### Post by MG&amp;TL on 2012-07-19
Ah. That would be why. 

Run these commands, in this order, from a fresh terminal.

```
sudo apt-get install gcc build-essential
```You'll need a C compiler to build from source.

```
cd ~/Desktop/zach
``````
sudo su
```Note the 's'- 'du' is unfortunately a legal command that does something entirely different to what you want (disk usage, actually), whereas you want 'su' which gives you temporary full root access.

```
make clean
``````
make
``````
make install
```Finally, logout of root so you can't do anything damaging:

```
exit
```

Give us the output from that, and we'll go from there.

---

### Post by fatboy07 on 2012-07-19
> **MG&TL said:**
> Ah. That would be why. 

Run these commands, in this order, from a fresh terminal.

```
sudo apt-get install gcc build-essential
```You'll need a C compiler to build from source.

```
cd ~/Desktop/zach
``````
sudo su
```Note the 's'- 'du' is unfortunately a legal command that does something entirely different to what you want (disk usage, actually), whereas you want 'su' which gives you temporary full root access.

```
make clean
``````
make
``````
make install
```Finally, logout of root so you can't do anything damaging:

```
exit
```

Give us the output from that, and we'll go from there.

thank you for the big help from you and chilli, :) I've already giving up but when i try again the modprobe rt5370sta kaboom! it works! thank you so much for the help. cheers! :)

---

### Post by MG&amp;TL on 2012-07-19
> **fatboy07 said:**
> thank you for the big help from you and chilli, :) I've already giving up but when i try again the modprobe rt5370sta kaboom! it works! thank you so much for the help. cheers! :)

Woot!

Great, good luck with your *buntu. Might be worth bookmarking this page in case of reinstalls or whatever. :)

---

