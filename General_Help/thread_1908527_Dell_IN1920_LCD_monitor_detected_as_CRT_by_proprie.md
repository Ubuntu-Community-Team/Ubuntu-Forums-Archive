---
title: "Dell IN1920 LCD monitor detected as CRT by proprietary nVidia driver"
date: 2012-01-13
forum: General Help
---

### Post by rick_james on 2012-01-13
Hi. I am a newbie to Linux but just installed Lubuntu 11.10.

I then went to "Additional Drivers" and installed the recommended proprietary nVidia driver.

After installation it thinks my Dell IN1920 LCD monitor (analog) is a CRT monitor and forces it to 1024x768.

How do I uninstall the nVidia proprietary driver and get back my 1366x768 @60Hz resolution?
 
Thank you in advance. 

Paul

---

### Post by rick_james on 2012-01-13
I successfully uninstalled the nVidia drivers and rebooted.

Now I am in 1366x768 @60Hz resolution.

I need to edit my /etc/X11/xorg.conf file.

Here is what my xorg.conf says now:


Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection

How can I add a modeline or specify 1360x768?

My monitor works best at 1360x768 rather than at 1366x768.

Thanks! :-)

---

### Post by rick_james on 2012-01-14
I managed to force my monitor to display as 1360x768 @60Hz using the open source nouveau driver. 

I edited my /etc/X11/xorg.conf file and added these values to get it to work:


```
Section "Monitor"
	Identifier "DELL IN1920"
	Option "PreferredMode" "1360x768_60.00"
	HorizSync	30-83
	VertRefresh	50-75
	VendorName      "Dell"	
	Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync
EndSection 

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5500]"
	BoardName	"nvidia"
	VendorName      "NVIDIA Corporation"
	Option		"NoLogo" "True"
EndSection

Section "Screen" 
        Device "nVidia Corporation NV34 [GeForce FX 5500]" 
        Identifier "Default Screen" 
        Monitor "DELL IN1920" 
        DefaultDepth 24 
        SubSection "Display" 
               Depth 24 
               Modes "1360x768_60" 
        EndSubSection    
EndSection

```
 
What I would like to do is install the nVidia driver from 'Additional Drivers' so I can get 3D acceleration.  Is it necessary to install the nVidia driver?  I don't play 3D games.  I just watch XviD videos and listen to music.  

Will the nVidia driver improve 2D performance?  I would like to use GIMP and wonder if I need that driver or would the default open source nouveau driver suffice?

My monitor is a Dell IN1920 LCD with only an analog VGA output to my nVidia GeForce FX 5500 AGP 8x video card.

If I use the nVidia driver it will detect my Dell LCD monitor as a CRT because of the analog VGA connection and will force it to 1024x768 so it doesn't look right.  I tried Puppy Linux and it also detects it as CRT if I use the nVidia driver.
 
I read the Ubuntu forums and a few other people are asking the same questions.  I think someone managed to edit their xorg.conf file to make it work with the nVidia proprietary driver and get native resolution even on their analog VGA output from LCD monitor.
 
Thanks for any help.  I greatly appreciate it.  Thus far I am _very_ impressed with Lubuntu.  It is elegant in appearance for a Linux distro and fast! :-)
 
Paul

---

### Post by rick_james on 2012-01-14
Okay, I finally solved this problem after reading this thread here:
[http://ubuntuforums.org/showpost.php?p=5305439&postcount=32](http://ubuntuforums.org/showpost.php?p=5305439&postcount=32)

I added Option "ModeValidation" "NoMaxPClkCheck" under 'Devices', installed the latest nVidia proprietary drivers and all is well.

It is running at 1360x768 @50Hz. It should be 60Hz but I was able to raise it to 53Hz, which is still within my monitor's specifications so I hope it won't hurt it.

I hope this helps someone else.

:D

Paul

---

### Post by fleamour on 2012-01-14
Glad to see I'm not the only one who answers their own posts!  [I have to crystallize my own ideas in written form to troubleshoot.]

May wanna mark thread as solved...

---

