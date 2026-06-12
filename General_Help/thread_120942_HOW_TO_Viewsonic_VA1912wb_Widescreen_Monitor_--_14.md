---
title: "HOW TO: Viewsonic VA1912wb Widescreen Monitor -- 1440x900 Support"
date: 2006-01-23
forum: General Help
---

### Post by lysis on 2006-01-23
i spent 5 hours trying to figure this out since this is a 16:10 monitor (not the norm) and i couldn't figure out how to default to the 1440x900. i found a couple posts that helped me get the information posted. please follow directions as listed and this should be all you need to do.



install fglrx as instructed by the wiki (directions below for ease of use)

```
Ubuntu provided drivers

   1.

      Install the kernel drivers. These drivers should be installed by default, but it's better to make sure they are installed. You need the package linux-$arch, where you replace $arch by the CPU architecture for the machine. This is 386 or 686 for Intel pentium, 386 or K7 for AMD athlon.

sudo apt-get install linux-686

   2.

      Install the xorg-driver-fglrx package:

sudo apt-get install xorg-driver-fglrx

   3.

      Add fglrx to /etc/modules:

echo fglrx | sudo tee -a /etc/modules

   4.

      Change 'ati' to 'fglrx' in /etc/X11/xorg.conf

sudo sed -e 's/"ati"/"fglrx"/' -i /etc/X11/xorg.conf

   5.

      Restart your computer

```

after rebooting your computer, open up a terminal.  in the terminal type the commands ```
sudo cp /etc/X11/xorg.conf xorg.conf.BACKUP
sudo gedit /etc/X11/xorg.conf
```

with gedit open, replace the MONITOR section with the following:

```
Section "Monitor"
	Identifier	"VA1912wSERIE"
	HorizSync	30-82
	VertRefresh	50-85
	Option		"DPMS"
	Modeline 	"1440x900@75" 146.10 1440 1472 2024 2056 900 917 928 946
EndSection
```

now i'm not sure if it's needed, but i also have added to the 24bit the resolution 1440x900.  verify that the "default depth" is 24bit. if it's not, either change it, or just apply this information to the correct depth.

```
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
```



please post any questions, but this is ALL i needed to do to get this monitor working.

---

### Post by tvgm2 on 2006-02-19
What if you have an Nvidia card?

---

### Post by lysis on 2006-03-02
i got an nvidia now.  just as easy.   install the latest drivers for nvidia and it should already be an option in the list.

---

### Post by ahh_dee on 2006-03-02
neat im going to try this on my 42'' tv screen

---

### Post by theraginasian on 2006-05-02
Just to try and be helpful, here is what I have found to work by using the GooglePlex...

```

Section "Monitor"
	Identifier	"VA1912wb"
	HorizSync 	30.0 - 82.0
	VertRefresh 	50.0 - 85.0
	Option		"DPMS"
	Modeline 	"1440x900_70.00" 126.98 1440 1536 1688 1936 900 901 904 937 -HSync +Vsync
	Modeline 	"1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
	DisplaySize 	1440 900
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV41.1 [GeForce 6800]"
	Monitor		"VA1912wb"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1440x900_70.00" "1440x900_60.00"
	EndSubSection
EndSection

```

---

### Post by Noremacam on 2006-05-18
How do I make this work with an i810 intel chipset? The computer seems to ignore the resolutions that I specify in the xorg.conf. I tried copying theraginasian's code(with the exception of parts of the screen section, since I have an i810 based graphics card).

---

### Post by Jacob Geri on 2006-05-18
get the debian repository for 810resolution (i think), or upgrade to dapper and get 915resolution (this is what i used). Install this, then change the resolution in m5 to whatever resolution you want. you can even edit bits per pixel!

---

### Post by roxics on 2006-06-27
I have the same monitor and the same problem, so I'm glad I found this thread. However my ATI card is a 7500 series Radeon VE Dual Display. I've heard the ATi driver set won't work for cards older then the 8500 series. 

Should I still try this anyway or is there another solution for me?

I'm using 6.06

---

### Post by amoore on 2006-07-05
[QUOTE=theraginasian]Just to try and be helpful, here is what I have found to work by using the GooglePlex...

```

Section "Monitor"
	Identifier	"VA1912wb"
	HorizSync 	30.0 - 82.0
	VertRefresh 	50.0 - 85.0
	Option		"DPMS"
	Modeline 	"1440x900_70.00" 126.98 1440 1536 1688 1936 900 901 904 937 -HSync +Vsync
	Modeline 	"1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
	DisplaySize 	1440 900
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV41.1 [GeForce 6800]"
	Monitor		"VA1912wb"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1440x900_70.00" "1440x900_60.00"
	EndSubSection
EndSection

```[/QUOTE]

theraginasian you are a god among men your xorg.conf listed above worked fantastic for my VA1912wb and nvidia 5200.

---

### Post by prolynx on 2006-07-14
found this on another forum

[http://www.omegadrivers.net/](http://www.omegadrivers.net/)

---

### Post by strumer on 2006-07-18
Just did this in dapper and it worked great.  (nvidia)

The font size was small on the login screen so I edited /usr/share/gdm/themes/Human/gtk-2.0/gtkrc

changed the font name attribute to
 font_name = "Sans 36"

Don't know if this is the best way or not.. but it worked for me on the Human theme.

---

### Post by jISh on 2006-07-29
> **theraginasian said:**
> Just to try and be helpful, here is what I have found to work by using the GooglePlex...

```

Section "Monitor"
	Identifier	"VA1912wb"
	HorizSync 	30.0 - 82.0
	VertRefresh 	50.0 - 85.0
	Option		"DPMS"
	Modeline 	"1440x900_70.00" 126.98 1440 1536 1688 1936 900 901 904 937 -HSync +Vsync
	Modeline 	"1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
	DisplaySize 	1440 900
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV41.1 [GeForce 6800]"
	Monitor		"VA1912wb"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1440x900_70.00" "1440x900_60.00"
	EndSubSection
EndSection

```

This worked perfectly, using nVidia and the exact same monitor. Kudos!

---

### Post by veritas366 on 2006-08-08
Hello...I have this exact monitor.  On sale really cheap at Tiger Direct.  However the fix didn't work.  I'm actually running Mepis, but that uses the Ubuntu repos now, so I think this should be relevant.  I got a "undefined reference to screen 0" error.  I commented out the reference to screen   0 at the top and instead got a "no screens error."

Here's my xorg as it looked when I made the edits:

> Section "ServerLayout"
  Identifier "XFree86 Configured"
  Screen 0 "Screen0" 0 0
 #Screen 0 "ATIScreen" 0 0
  InputDevice "Keyboard0" "CoreKeyboard"
  InputDevice "PS/2 Mouse" "CorePointer"
 #InputDevice "USB Mouse" "CorePointer"
 #InputDevice "Touchpad" "CorePointer"
 #InputDevice "Stylus" "CorePointer"
 #InputDevice "Eraser" "CorePointer"
 #InputDevice "Cursor" "CorePointer"
 #InputDevice "Serial Mouse" "CorePointer"
EndSection



Section "Module"
  Load "GLcore"
  Load "bitmap"
  Load "dbe"
  Load "ddc"
  Load "dri"
  Load "extmod"
  Load "freetype"
  Load "glx"
  Load "int10"
  Load "record"
  Load "type1"
  Load "v4l"
  Load "vbe"
  Load "synaptics"
EndSection

<skipping all the stuff about input devices>

Section "Monitor"
   Identifier   "VA1912wb"
   HorizSync    30.0 - 82.0
   VertRefresh    50.0 - 85.0
   Option      "DPMS"
   Modeline    "1440x900_70.00" 126.98 1440 1536 1688 1936 900 901 904 937 -HSync +Vsync
   Modeline    "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
   DisplaySize    1440 900
EndSection


Section "Device"
  Identifier  "Card0"
  Driver "nvidia"
  BoardName "unknown"

 #BusID  "PCI:1:0:0"
 #Option "sw_cursor" # needed for some ati cards
 #Option "hw_cursor"
 #Option "NoAccel"
 #Option "ShowCache"
 #Option "ShadowFB"
 #Option "UseFBDev"
 #Option "Rotate"
  Option "UseInternalAGPGART" "no"

# savage special options, use with care
 #Option "NoUseBios"
 #Option "BusType" "PCI"
  Option "DmaMode" "None"

# nvidia special options, use with care
  Option "CursorShadow" "1"
  Option "CursorShadowAlpha" "63"
  Option "CursorShadowYOffset" "2"
  Option "CursorShadowXOffset" "4"
  Option "FlatPanelProperties" "Scaling = native"
  Option "NoLogo" "false"
  Option "IgnoreEdid" "true" # needs to be true for some nvidia cards
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Card0"
  Monitor "VA1912wb"
  DefaultColorDepth 24
 
  SubSection "Display"
      Depth      24
      Modes      "1440x900_70.00" "1440x900_60.00"
   EndSubSection
 
  # Only the official NVIDIA driver supports twinview
  # these setting are an example
  Option "TwinView" "false"
  Option "SecondMonitorVendorName" "unknown"
  Option "SecondMonitorModelName" "unknown"
  Option "SecondMonitorHorizSync" "30-75"
  Option "SecondMonitorVertRefresh" "50-70"
 #Option "MetaModes" "1024x768, 1024x768"
  Option "TwinViewOrientation" "RightOf"
  Option "ConnectedMonitor" "dfp,dfp"
EndSection



Section "DRI"
  Mode 0666
EndSection


What did I do wrong?  Thanks.

---

### Post by raguru on 2006-08-16
I finally got my Viewsonic VA1912wb monitor to work yesterday.  I installed Ubuntu 6.06 just last weekend.  

I initially tried the different things posted here, but each time when I rebooted, I would get a fatal error with the XServer and I would be given only a text login with no graphics.  Each time, I would restore the backup of the xorg.conf file and try something else.  

I then installed the NVIDIA drivers since I have a GeForce 6200 AGP graphics card from Method 1 mentioned in this link:

[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

Then when I looked in /var/log/xorg.0.log, I found that it had detected my graphics card correctly and even my monitor correctly.  So, I decided I did not have to do too many changes in the xorg.conf file.  Here are the changes I made to the xorg.conf file after making a backup, of course:

Under Section "Monitor" I added
        HorizSync 	30.0 - 82.0
	VertRefresh 	50.0 - 85.0

Under Section "Screen", the default depth was already set to 24.  So, under Subsection "Display" Depth 24, the previous entries were as follows:

"1024x768" "832x624" "800x600"

To that I added 1440x900 as shown below:

"1440x900" "1024x768" "832x624" "800x600"

When I logged out and pressed Ctrl-Alt-Backspace to restart the XServer, voila, everything was nice and crisp in 1440x900! :o

Please post if you have any questions.

---

### Post by utdjohn on 2006-09-12
Hello.  I've tried just about everything mentioned in this thread, as well as other places... Still no luck.  No matter what, I get 1024x768.

- Fresh install of Ubuntu 6.06
- Thinkpad T40
- Radeon Mobility M7 LW (7500)
- Viewsonic VA1912wb

- Tried first with default drivers (ati), and then installed the DRI Radeon drivers from [http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/)

- DRI drivers seemed to work because I get no errors and:
glxinfo | grep render -> 
direct rendering: Yes
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 4x x86/MMX/SSE2 TCL

- Have tried many xorg.conf combinations.  Currently, I have commented out all diplay modes except 1440x900

- But no matter what I do, it goes to 1024x768, which is also what the "Screen Resolution" dialog says.  The funny thing is, it also says the refresh rate is -25862 Hz.

- Here's my config.  I deleted out all the other display depths for brevity, but I had each of them with the "1024x768" option only.  I also took them out all together and this made no difference.  I figure my card should be able to support the 24bit depth, which is what I have the default pointing to.

Thanks in advance!!

Section "Device"
        Identifier      "Radeon Mobility M7 LW"
        Driver          "radeon"
        VendorName      "ATI Technologies Inc."
        BoardName       "Radeon Mobility M7 LW"
        BusID           "PCI:1:0:0"
        Option          "AGPMode"       "4"
        Option          "AGPFastWrite"  "true"
        Option          "EnablePageFlip"        "true"
EndSection

Section "Monitor"
  Identifier "VA1912wb"
  HorizSync 30-82
  VertRefresh 50-85
  Option "DPMS"
  Modeline "1440x900@75" 146.10 1440 1472 2024 2056 900 917 928 946
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon Mobility M7 LW"
	Monitor		"VA1912wb"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		#Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
		#Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "832x624" "800x600" "720x400" "640x640" "640x480"
		Modes		"1440x900" 
	EndSubSection

EndSection

---

### Post by SVWander on 2007-02-19
> **lysis said:**
> i spent 5 hours trying to figure this out since this is a 16:10 monitor (not the norm) and i couldn't figure out how to default to the 1440x900. i found a couple posts that helped me get the information posted. please follow directions as listed and this should be all you need to do.



install fglrx as instructed by the wiki (directions below for ease of use)

[code]Ubuntu provided drivers

   1.

      Install the kernel drivers. These drivers should be installed by default, but it's better to make sure they are installed. You need the package linux-$arch, where you replace $arch by the CPU architecture for the machine. This is 386 or 686 for Intel pentium, 386 or K7 for AMD athlon.

sudo apt-get install linux-686

   2.

      Install the xorg-driver-fglrx package:

sudo apt-get install xorg-driver-fglrx

   3.

      Add fglrx to /etc/modules:

echo fglrx | sudo tee -a /etc/modules

   4.

      Change 'ati' to 'fglrx' in /etc/X11/xorg.conf

sudo sed -e 's/"ati"/"fglrx"/' -i /etc/X11/xorg.conf

   5.

      Restart your computer
[

Well, when I rebooted xorg was not working. Since I am new to Ubuntu I have no idea how to copy the error message that it allowed me to see. I reversed the instructions to:

sudo sed -e 's/"fglrx"/"ati"/' -i /etc/X11/xorg.conf

hopefully I got it typed in correctly . . . rebooted. There was a much short message when xorg didn't load . . . can anyone tell me how to get back into Ubuntu. 
the machine is a gateway with a 
Celeron CPU 2.40GHz
Nvidia GeForce4 MX 440
UPDATE: I was able to get xorg.conf back to the way it was before I started messing with it. I looked at the copy of xorg.conf in C Live and didn't find a reference to ati and when I looked at the either the one is CD Live or in the one I tried to modify. So I am back to where I started.

---

### Post by il-luzhin on 2007-04-17
I still can't get my sis730 integrated video to work with viewsonic vx1945wm.  I have downloaded a driver from [www.sis.com](www.sis.com) but don't know how or where to install a driver that isn't in a package download.  Someone please save me.

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-82 
	VertRefresh	50-85
	Modeline 	"1440x900@75" 146.10 1440 1472 2024 2056 900 917 928 946
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

