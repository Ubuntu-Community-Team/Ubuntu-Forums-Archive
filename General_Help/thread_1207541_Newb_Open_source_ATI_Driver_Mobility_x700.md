---
title: "Newb Open source ATI Driver Mobility x700"
date: 2009-07-08
forum: General Help
---

### Post by Mechmechie on 2009-07-08
Hi I am trying to get improved graphics on my Ati Radeon Mobitily X700,on jaunty. So I followed the instructions for installing the open source ATI drivers. But on restarting X server I get an error sayingit is running in low graphics mode and gives me option to repair or view the errors etc.

From the logs it fails in the ""Undefined InputDevice "Generic Keyboard" referenced by ServerLayout "Default Layout"."
I referenced this out and then it failed in the mouse section.

How do I find out what the input device settings are?
Thanks

My current xorg.conf
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
 

********************************************

My trial version of xorg.conf
Section "Device"
	Identifier	"X700"
	Driver		"ati"
	BusID		"PCI:1:0:0"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"X700"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Modes		"1440x900" "1024x768"
	EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection



****************************************************************

Xorg.0.log

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux james-laptop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul  7 22:01:41 2009
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
	Undefined InputDevice "Generic Keyboard" referenced by ServerLayout "Default Layout".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log

**************************************************

Thanks for any help

---

### Post by Woody1987 on 2009-07-08
ubuntu by default uses the open source drivers for your card. They will be the best drivers you can use as ATI no longer supports your card so there will be no official drivers from them anymore.

---

### Post by Mechmechie on 2009-07-09
Thanks for  the reply. 
My xorg.conf file says i am using a vesa driver. This gives no 3d support by the looks of things.
I cant play 3d chess,etc.which is why I am trying to use the open source ati radeon drivers
Under windows this card can play Doom 3d at reasonable settings. So is this the best that I can expect from my card under Ubuntu?

The instructions say the x700 is supported by the open source drivers.

---

