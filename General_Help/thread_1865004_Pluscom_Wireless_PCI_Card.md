---
title: "Pluscom Wireless PCI Card"
date: 2011-10-19
forum: General Help
---

### Post by bzzzzz on 2011-10-19
I recently bought this wireless pci card and I've managed to get it working
using the windows drivers that came with the machine and ndiswrapper.

However when browsing through the disk that came with the card I noticed a folder saying linux drivers.  

However there where no instructions so I was confused as to how to continue.

As I've got it working is there any point in trying to install the linux drivers for it and get it working that way.

How would I go about installing the linux drivers for the card.  (I know that I need the .inf file when using ndiswrapper, but I have no clue what a linux driver file looks like)

Thanks

Pete

---

### Post by hal8000 on 2011-10-19
With every hardware containing drivers for multiple platforms, there is usually an install or readme file.
This would be the best place to start, and post back any instructions you dont understand.

It's also possible that the Ubuntu kernel already knows about your card,
so in your next reply, please post output from these commands:

lspci

iwconfig

---

### Post by bzzzzz on 2011-10-19
[B]* README
[/B]
*

* Ralink Tech Inc.

* 

* [http://www.ralinktech.com](http://www.ralinktech.com)

*



=======================================================================

ModelName:

===========

RT61 Wireless Lan Linux Driver





=======================================================================

Driver lName:

===========

rt61.o/rt61.ko





=======================================================================

Supporting Kernel:

===================

linux kernel 2.4 and 2.6 series. 

Tested in Redhat 7.3 or later.





=======================================================================

Description:

=============

This is a linux device driver for Ralink RT61 a/b/g WLAN Card.





=======================================================================

Contents:

=============

Makefile.4	        : Makefile for kernel 2.4 series

Makefile.6	        : Makefile for kernel 2.6 series

Makefile.RTL865x	: Makefile for big endian platform

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



1> $tar -xvzf RT61_Linux_STA_Drv_x.x.x.x.tar.gz

    go to "./RT61_Linux_STA_Drv_x.x.x.x/Module" directory.

    

2> $cp Makefile.4  ./Makefile       # [kernel 2.4]

    or

   $cp Makefile.6  ./Makefile       # [kernel 2.6]

    or

   $cp Makefile.RTL865x ./Makefile  #  big endian platform

   

3> [kernel 2.4]

    $chmod 755 Configure

    $make config         # config build linux os version



4> $make all            # compile driver source code

4.1> $make install



5> $cp rt2561.bin /etc/Wireless/RT61STA/	# copy firmware

   $cp rt2561s.bin /etc/Wireless/RT61STA/

   $cp rt2661.bin /etc/Wireless/RT61STA/



6>  $dos2unix rt61sta.dat

    $cp rt61sta.dat  /etc/Wireless/RT61STA/rt61sta.dat       

    # !!!check if it is a binary file before loading !!!  

    

7> $load                

    #[kernel 2.4]

    #    $/sbin/insmod rt61.o

    #    $/sbin/ifconfig ra0 inet YOUR_IP up

        

    #[kernel 2.6]

    #    $/sbin/insmod rt61.ko

    #    $/sbin/ifconfig ra0 inet YOUR_IP up



        

Note: Script functionality:

load            load module to kernel

unload          unload module from kernel

Configure       retrieve linux version 





=======================================================================

CONFIGURATION:  

====================

RT61 driver can be configured via following interfaces, 

i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file,

     (iv)RaConfig61



i)  iwconfig comes with kernel.  

ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.

iii)copy configuration file "rt61sta.dat" to /etc/Wireless/RT61STA/rt61sta.dat.

iv) RaConfig61 is utility for rt61.

           

Configuration File : rt61sta.dat

---------------------------------------

# Copy this file to /etc/Wireless/RT61STA/rt61sta.dat

# This file is a binary file and will be read on loading rt.o module.

#

# Use "vi -b rt61sta.dat" to modify settings according to your need.

# 

# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure

# 2.) set Channel to "0" for auto-select on Infrastructure mode

# 3.) set SSID for connecting to your Accss-point.

# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"

# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"

# for more information refer to the Readme file.

# 

# The word of "[Default]" must not be removed

[Default]

CountryRegion=0

CountryRegionABand=7

WirelessMode=0

SSID=AP350

NetworkType=Infra

Channel=0

AuthMode=OPEN

EncrypType=NONE

DefaultKeyID=1

Key1Type=0

Key1Str=0123456789

Key2Type=0

Key2Str=

Key3Type=0

Key3Str=

Key4Type=0

Key4Str=

WPAPSK=abcdefghijklmnopqrstuvwxyz

TxBurst=0

PktAggregate=0

WmmCapable=0

APSDCapable=0

APSDAC=0;0;0;0

BGProtection=0

ShortSlot=0

IEEE80211H=0

TxRate=0

RTSThreshold=2347

FragThreshold=2346

PSMode=CAM

TxPreamble=0

FastRoaming=0

NativeWpa=1



-----------------------------------------------

*NOTE:

WMM parameters:

1.) WmmCapable			

    Set it as 1 to turn on WMM Qos support

	

2.) APSDCapable

	Set it as 1 to use automatic power-save delivery(APSD) on an Non-AP QSTA



3.) APSDAC

	Set ACs corresponding BE, BK, VI and VO as delivery-enabled or delivery-disabled



	

All WMM parameters do not support iwpriv command but WmmCapable, 

	please store all parameter to rt61sta.dat, and restart driver. 	







NetworkManager and WPS:

If Native WPA Supplicant (NetworkManager) is enabled, WPS CAN NOT be triggered.

For this case, we have to set NativeWpa=1 in rt61sta.dat.

Otherwise, if we want to use WPS, we have to disable NetworkManager by setting

NativeWpa=0 in rt61sta.dat.



-----------------------------------------------

syntax is 'Param'='Value' and describes below. 



1. CountryRegion=value                                 

	value

		0: use 1 ~ 11 Channel

		1: use 1 ~ 13 Channel

		2: use 10, 11 Channel

		3: use 10 ~ 13 Channel

		4: use 14 Channel

		5: use 1 ~ 14 Channel

		6: use 3 ~ 9 Channel

		7: use 5 ~ 13 Channel

   	 	                                      

2. CountryRegionABand=value      							

	value	

		0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel

		1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel

		2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel

		3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel

		4: use 149, 153, 157, 161, 165 Channel

		5: use 149, 153, 157, 161 Channel

		6: use 36, 40, 44, 48 Channel

		7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel

		8: 52, 56, 60, 64 Channel

		9: 34, 38, 42, 46 Channel

		10: 34, 36, 38, 40, 42, 44, 46, 48, 52, 56, 60, 64 Channel

                                                   

3. SSID=value                	

	value

		0~z, 1~32 ascii characters.

                    	

4. WirelessMode=value

	value	

		0: 11b/g mixed 

		1: 11B only 

		2: 11A only          //Support in RfIcType=1(id=RFIC_5225) or RfIcType=2(id=RFIC_5325)

		3: 11a/b/g mixed     //Support in RfIcType=1(id=RFIC_5225) or RfIcType=2(id=RFIC_5325)

		4: 11G only

		

5. TxRate=value

	value

		 0: Auto    	//WirelessMode=0~4	

		 1: 1 Mbps	 	//WirelessMode=0 or 1 or 3

         2: 2 Mbps	 	//WirelessMode=0 or 1 or 3

         3: 5.5 Mbps 	//WirelessMode=0 or 1 or 3

         4: 11 Mbps 	//WirelessMode=0 or 1 or 3

         5: 6  Mbps  	//WirelessMode=0 or 2 or 3 or 4

         6: 9  Mbps  	//WirelessMode=0 or 2 or 3 or 4

         7: 12 Mbps  	//WirelessMode=0 or 2 or 3 or 4

         8: 18 Mbps  	//WirelessMode=0 or 2 or 3 or 4

         9: 24 Mbps  	//WirelessMode=0 or 2 or 3 or 4

        10: 36 Mbps  	//WirelessMode=0 or 2 or 3 or 4

        11: 48 Mbps  	//WirelessMode=0 or 2 or 3 or 4

        12: 54 Mbps  	//WirelessMode=0 or 2 or 3 or 4

 	                                       

6. Channel=value

	value

		depends on CountryRegion or CountryRegionABand

                    	

7. BGProtection=value

	value

		0: Auto 

		1: Always on 

		2: Always off

                    	

8. TxPreamble=value

  	value

		0:Preamble Long

		1:Preamble Short 

		2:Auto

                    	

9. RTSThreshold=value

	value

		1~2347                                                       

                    	                                       

10. FragThreshold=value

	value       	

		256~2346

                    	

11. TxBurst=value

	value

		0: Disable

		1: Enable



12. NetworkType=value	    		

	value 

		Infra: infrastructure mode

       	Adhoc: adhoc mode

                                                                                                                                                        	                                                          

13. AuthMode=value

	value

		OPEN	 	For open system	

		SHARED	  	For shared key system	

		WEPAUTO     Auto switch between OPEN and SHARED

		WPAPSK      For WPA pre-shared key  (Infra)

		WPA2PSK     For WPA2 pre-shared key (Infra)

		WPANONE		For WPA pre-shared key  (Adhoc)

		WPA         Use WPA_Supplicant

		WPA2        Use WPA_Supplicant



14. EncrypType=value

	value

		NONE		For AuthMode=OPEN                    

		WEP			For AuthMode=OPEN or AuthMode=SHARED 

		TKIP		For AuthMode=WPAPSK or WPA2PSK                    

		AES			For AuthMode=WPAPSK or WPA2PSK                     

		

15. DefaultKeyID=value

	value

		1~4



16. Key1=value

    Key2=value

    Key3=value

    Key4=value

	value

		10 or 26 hexadecimal characters eg: 012345678

        5 or 13 ascii characters eg: passd

    (usage : "iwpriv" only)     



17. Key1Type=vaule

    Key2Type=value

    Key3Type=vaule

    Key4Type=vaule

    value

		0   hexadecimal type

		1   assic type

    (usage : reading profile only)



18. Key1Str=value

    Key2Str=value

    Key3Str=vaule

    Key4Str=vaule

    value

		10 or 26 characters (key type=0)

		5 or 13 characters  (key type=1)

    (usage : reading profile only)	



19. WPAPSK=value              	

	value

		8~63 ASCII  		or 

		64 HEX characters



20. PktAggregate=value

	value

		0: Disable

		1: Enable when the peer supports it

																

21. WmmCapable=value

	value

		0: Disable WMM

		1: Enable WMM

        

22. PSMode=value

    value

    	CAM			    Constantly Awake Mode

		Fast_PSP		Power Save Mode

		MAX_PSP			Max power save mode

		

23. IEEE80211H=value

	value

		0:	Disable

		1:	Enable	Spectrum management

		(This field can be enable only in A band)

		

24. FastRoaming=value				

	value

		0: Disable Fast Roaming

		1: Enable Fast Roaming



25. RoamThreshold=value

	value [Valid on FastRoaming=1]      	

		60~90



26. APSDCapable=value

	value [Valid on WmmCapable=1]

		0: Disable APSD

		1: Enable APSD



27. APSDAC=value

	value [Valid on APSDCapable=1]

		0: Delivery-disabled AC 

		1: Delivery-enabled AC

	

		//========================//

		AC_BE  AC_BK  AC_VI  AC_VO

		{0, 1};{0, 1};{0, 1};{0, 1}

        //========================//







MORE INFORMATION

=================================================================================

If you want for rt61 driver to auto-load at boot time:

A) choose ra0 for first RT61 WLAN card, ra1 for second RT61 WLAN card, etc.

 

B) go to "./RT61_Linux_STA_Drv_x.x.x.x/Module" directory.

   $make install



NOTE:

	if you use dhcp, 

	add this line

	BOOTPROTO='dhcp'

	in the file ifcfg-ra0 .





*C) To ease the Default Gateway setting, 

    add the line

    GATEWAY=x.x.x.x   

    in /etc/sysconfig/network



D) When build for SUSE, please unmark the part for SUSE in Makefile.

   When build for Mandriva 2007.1, please unmark the part for Mandriva in Makefile.

**The response to lspci is **

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:05.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
00:06.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

[B]
and the response to iwconfig is[/B] 

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"chocolate"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:26:F2:09:E0:28   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:111   Missed beacon:0

---

### Post by mikeatvillage on 2011-12-18
I have one of these (from eBay) and my system recognised it OK - didn't have to use the CD to install it. Ubuntu Desktop 10.04LTS/11.04/11.10 

The user manual on the miniCD doesn't mention Linux installation at all but I'd assume that the usual configure/make/make install would be all that's required.

---

