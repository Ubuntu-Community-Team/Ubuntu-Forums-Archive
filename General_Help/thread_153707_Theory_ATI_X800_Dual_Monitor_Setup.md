---
title: "Theory: ATI X800 Dual Monitor Setup"
date: 2006-04-01
forum: General Help
---

### Post by BeerSlinger on 2006-04-01
Hi all,

I just want to check on something because I'm not sure how Ubuntu handles it.  Basically I have an ATI X800 XL with a dual monitor setup.  I have found the “How To’s” on how to utilize this but I have a question when it comes to theory and practice because the more I think about it, the less I’m sure it is worth the time and the effort to do it…

The question basically is, how does Ubuntu handle the recognition of two monitors?

In windows I have it setup to extend from one monitor and the desktop extends to the other monitor.  The reason why I’m not sure if this will work is because of the disparity in the size of the two.  One is a 21 inch and the other is a 16 inch.  The 21 has a resolution of 1280X1024 and the 16 has an 800X600 respectively.  So, can Ubuntu handle the disproportion of the screen resolutions? Also, does it show the same desktop twice or is there a way to utilize and extend the desktop so it is larger…

Since this question has come up in my mind, I have to question if resolving this is even practical given the imbalance of the sizes of the monitors…

But I don’t myself from theory to practice…could someone shed some light on this subject?

---

### Post by DOtSlaSHuCantCME on 2006-04-01
[QUOTE=BeerSlinger]Hi all,

I just want to check on something because I'm not sure how Ubuntu handles it.  Basically I have an ATI X800 XL with a dual monitor setup.  I have found the &#8220;How To&#8217;s&#8221; on how to utilize this but I have a question when it comes to theory and practice because the more I think about it, the less I&#8217;m sure it is worth the time and the effort to do it&#8230;

The question basically is, how does Ubuntu handle the recognition of two monitors?

In windows I have it setup to extend from one monitor and the desktop extends to the other monitor.  The reason why I&#8217;m not sure if this will work is because of the disparity in the size of the two.  One is a 21 inch and the other is a 16 inch.  The 21 has a resolution of 1280X1024 and the 16 has an 800X600 respectively.  So, can Ubuntu handle the disproportion of the screen resolutions? Also, does it show the same desktop twice or is there a way to utilize and extend the desktop so it is larger&#8230;

Since this question has come up in my mind, I have to question if resolving this is even practical given the imbalance of the sizes of the monitors&#8230;

But I don&#8217;t myself from theory to practice&#8230;could someone shed some light on this subject?[/QUOTE]

=============================================================
I Just cant see myself with only one monitor after dual monitoring for a while now,the question you possed is in fact the setup i have,so yes it can be done,checkout my xconf setup,(checkout the screen area and video card section).

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device" 
  
	Driver		"i810"
	BusID		"PCI:0:2:0"
     EndSection

Section "Device"
        Identifier   " nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] "
        Driver           "nvidia"
        BusID            "PCI:01:09:0"
        Option "NoLogo" "true"
EndSection
       
Section "Monitor"
	Identifier	"COMPAQ FS755"
	Option		"DPMS"
EndSection

Section "Monitor"
        Identifier     "COMPAQ  150"
EndSection

Section "Screen"
	Identifier	"Screen 0"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"COMPAQ FS755"
	DefaultDepth        24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
        
Section   "Screen"
           Identifier    "Screen 1"
           Device   " nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] "

           Monitor      "COMPAQ 150"
           DefaultColorDepth  24
           SubSection "Display"
                    Depth      8
          Modes   "1024x768" "800x600" " 649x480"
          EndSubSection
          SubSection   "Display"
          Depth  16
          Modes    "1024x768" "800x600" "640x480"
          EndSubSection  
          SubSection   "Display"
          Depth      32
          Modes   "1024x768" "800x600" " 649x480"
          EndSubSection
                  
                  
        
  
           
          
EndSection                                     
              
     


Section "ServerLayout"
	Identifier	"Default Layout"
        Screen           "Screen 0"      
    	Screen		"Screen 1" RightOf "Screen 0" 
    	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

#Section "ServerFlags"
 #Option "Xinerama"  "true"
#EndSection
============================================================
you can manipulate your monitor resolution,color depth (if you ever have screen problems and stuff,my smaller monitor is set to 800x600 because i like the way apps looks all big and gaming is nice at that resolution,and my other monitor is at 1024x768 i surf on this monitor ect(more details fits your screen).

XINERAMA is what you will be putting in a section to get the extended desktop, where you can drag apps to and from desktops,i have XINERAMA off ,which gives me two identical desktop(just a personal choice)instead of extended desktops.


keep this or any other xconf file as a reference,because basically you will be
using the same setup but with your specs,pay close attention to the "monitor section"
and the "video card "section.

---

### Post by BeerSlinger on 2006-04-01
[QUOTE=DOtSlaSHuCantCME]=============================================================
I Just cant see myself with only one monitor after dual monitoring for a while now,the question you possed is in fact the setup i have,so yes it can be done,checkout my xconf setup,(checkout the screen area and video card section).

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device" 
  
	Driver		"i810"
	BusID		"PCI:0:2:0"
     EndSection

Section "Device"
        Identifier   " nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] "
        Driver           "nvidia"
        BusID            "PCI:01:09:0"
        Option "NoLogo" "true"
EndSection
       
Section "Monitor"
	Identifier	"COMPAQ FS755"
	Option		"DPMS"
EndSection

Section "Monitor"
        Identifier     "COMPAQ  150"
EndSection

Section "Screen"
	Identifier	"Screen 0"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"COMPAQ FS755"
	DefaultDepth        24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
        
Section   "Screen"
           Identifier    "Screen 1"
           Device   " nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] "

           Monitor      "COMPAQ 150"
           DefaultColorDepth  24
           SubSection "Display"
                    Depth      8
          Modes   "1024x768" "800x600" " 649x480"
          EndSubSection
          SubSection   "Display"
          Depth  16
          Modes    "1024x768" "800x600" "640x480"
          EndSubSection  
          SubSection   "Display"
          Depth      32
          Modes   "1024x768" "800x600" " 649x480"
          EndSubSection
                  
                  
        
  
           
          
EndSection                                     
              
     


Section "ServerLayout"
	Identifier	"Default Layout"
        Screen           "Screen 0"      
    	Screen		"Screen 1" RightOf "Screen 0" 
    	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

#Section "ServerFlags"
 #Option "Xinerama"  "true"
#EndSection
============================================================
you can manipulate your monitor resolution,color depth (if you ever have screen problems and stuff,my smaller monitor is set to 800x600 because i like the way apps looks all big and gaming is nice at that resolution,and my other monitor is at 1024x768 i surf on this monitor ect(more details fits your screen).

XINERAMA is what you will be putting in a section to get the extended desktop, where you can drag apps to and from desktops,i have XINERAMA off ,which gives me two identical desktop(just a personal choice)instead of extended desktops.


keep this or any other xconf file as a reference,because basically you will be
using the same setup but with your specs,pay close attention to the "monitor section"
and the "video card "section.[/QUOTE]

Oh, I knew it could be done.....I just wasn't sure if it was worth the effort......not when i'm so new and I have 1,000,000 other things to learn that are of greater importance.....Like: PHP, MySQL, Apache, Gnome Development........I'm kinda starting here from scratch....

But I can research it, I just wanted to make sure that it was time "Well Spent."

---

### Post by Ramses de Norre on 2006-04-01
It's very easy with an Nvidia card, but not with ati..
I've been trying to settle it up for my x600 but untill now, I haven't been able to configure it.. Let me now if you succeed ;)

---

### Post by BeerSlinger on 2006-04-01
[QUOTE=Ramses de Norre]It's very easy with an Nvidia card, but not with ati..
I've been trying to settle it up for my x600 but untill now, I haven't been able to configure it.. Let me now if you succeed ;)[/QUOTE]

Will do......that's kinda why I posed this question because I had tried it and it had been unsuccessfull so I had to really ask "was this worth my time," since it is, I'll give it another week or so......

Back to the grind stone.....

](*,)

---

### Post by jkeyes0 on 2006-04-03
I've got an X800 pro, and I'm not having any luck either. I'm trying to get the DVI to be the primary, as well. I've tried every other thread in here I could find, as well as some from the debian forums (googled it...). If you can come up with a good answer, please let us know!!

---

### Post by august on 2006-04-04
Bump. Looking for this myself. Have anyone gotten any further on this? I have a ati x800, but even tough i have set up two monitors, two screens, two devices and the RightOf thingy, the displays still mirror each other.

---

### Post by Firebird8 on 2006-04-09
have you tried running aticonfig on a terminal?

sudo aticonfig --initial=dual-head --screen-layout=right

---

### Post by Ramses de Norre on 2006-04-09
The best I've got was a working primary and a secondary which was recognized, initialized, no errors in the logs and on which I could move my mouse and place windows BUT the screen remained black, I could just place the windows into the black (so they disappeared) and get them back later.
I haven't got the aticonfig.. (command not found)

---

### Post by Firebird8 on 2006-04-10
Ramses de Norre aticonfig is for ati cards are you running a Nvidia?

---

### Post by Ramses de Norre on 2006-04-10
No, I have an ati x600 xt as I said before.
There is no program called aticonfig on my system and apt-cache search can't find it neither.

---

### Post by electrofreak66 on 2006-04-10
[QUOTE=Ramses de Norre]No, I have an ati x600 xt as I said before.
There is no program called aticonfig on my system and apt-cache search can't find it neither.[/QUOTE]
Do you have the ati drivers installed? Doesn't sound like it...
Here is what I did to get it working:

```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial=dual-head
```

reboot

confirm that your drivers are working:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5695 (8.23.7)
```

now install  the ATI control panel:

```
sudo apt-get install fglrx-control
```

if it still isn't working:
```
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```
and add fglrx module to the top of the list in /etc/modules

then reboot and it should work! It did for me.

---

### Post by Ramses de Norre on 2006-04-10
I use the fglrx drivers
```
ramses@icarus:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)


```
The symlink doesn't change anything, and the command still isn't found ```
ramses@icarus:~$ sudo aticonfig --initial=dual-head
sudo: aticonfig: command not found

```

---

### Post by august on 2006-04-10
I guess that the aticonfig is something that is included if you manually install the linux drivers from ati.com? Or?

---

### Post by electrofreak66 on 2006-04-10
aticonfig comes in the latest xorg-driver-fglrx package. if you have an older version driver then it would be fglrxconfig. 

What version driver do you have?

---

### Post by wilstoff on 2006-04-11
I've also been haveing a problem with my x800 pro and dual monitors.  I tried installing the drivers from ati.com but i then had problems with xwindows loading up.   So i just tried to do this
```

sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
```

and it said that 

"linux-restricted-modules-2.6.12-9-amd64-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded."

then for the xorgdriver it didn't find the xorg-driver-fglrx package.  Yes i did do a apt-get update too. 

I am definetly new at ubuntu so excessive explinations will help.

Thanks.

---

### Post by august on 2006-04-11
I will try this when I get home from vacation, and report back what happens when I try this.

---

### Post by wilstoff on 2006-04-17
I was playing around with the fglrxconfig yesterday and trying to see exactly what i could do.  For some reason fglrxconfig is the newest command that you can get from apt-get not aticonfig.  So i got some idea of fglrxconfig working where i can tell it is going to be in dual monitor mode, but the problem is that my second monitor just goes into power save mode and never comes back.  It doesn't want to turn on for some reason.  I looked into the xorg.conf then and found out that there wasn't even a second monitor definded there even though i clearly said to do dual monitors.  My guess is either fglrxconfig is broken and doesn't really turn on dual monitors just changes what the screen looks like on one, or some other program i can't tell is suppose to do that and is failing.  All i know is that before fglrxconfig i could see both monitors and they would both be the same screen.  Now i wish to revert back so i can just change the xinerama line so they would be one desktop.  Is there a default ubuntu setup driver that i can get back to what it was before?

---

### Post by Mnemonicman on 2006-04-18
Finally got dual monitors to work in Ubuntu. It's not quite what I had in mind though. What I do get is dual desktops. One in each monitor with no way to drag between the two. I'm happy that the 2nd monitor finally works but it would be very useful to just have the one desktop extended into the 2nd monitor. Oh and the command I used was "sudo aticonfig --initial=dual-head --screen-layout=right". I believe it was posted earlier in this thread.

---

### Post by electrofreak66 on 2006-04-18
[QUOTE=Mnemonicman]Finally got dual monitors to work in Ubuntu. It's not quite what I had in mind though. What I do get is dual desktops. One in each monitor with no way to drag between the two. I'm happy that the 2nd monitor finally works but it would be very useful to just have the one desktop extended into the 2nd monitor. Oh and the command I used was "sudo aticonfig --initial=dual-head --screen-layout=right". I believe it was posted earlier in this thread.[/QUOTE]

You can choose either. Dual-Head has two distict desktops running. Big Desktop mode lets you share windows amongst the screens. This sounds like it is what you want. To do that type:
```
sudo aticonfig --dtop=horizontal --overlay-on=1
```

---

### Post by Mnemonicman on 2006-04-18
Ah yes excellent. Thank you very much that was exactly what I needed.

---

### Post by august on 2006-04-18
I have created a detailed guide on how do do this, and for later reference i created a separate post for it. Read it here:

[http://ubuntuforums.org/showthread.php?p=935045](http://ubuntuforums.org/showthread.php?p=935045)

It would be nice if the topic starter could add a link to the solution in the first post of the topic, for searching and reference.

And I am a linux noob, so please come with corrections and suggestiens!

---

### Post by Hasen_A on 2007-01-05
Hello guys,

I also have an ATI X800GTO and have got the dual monitors up and running. I am able to move windows from left to right just as in windows using the xorg.conf pastet below. It works fine as long as I don't have an S-Video cable connected to my graphics card. Then my second monitor just goes into stand-by saying the settings are out of range.

I have tried changing Option "ModeX" , "HSyncX" and "VRefreshX" under Section Device from 2 to 3 with no result.

Any hints?
Thanks, Andy


```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Buttons"		"7"
	#Option		"Emulate3Buttons"	"true"
	Option		"ButtonMapping"		"1 2 3 6 7"
	#Option 		"Resolution"		"100"

EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 (R430 UO)"
	Driver		"fglrx"
	BusID		"PCI:5:0:0"
Option "DesktopSetup"  "horizontal,reverse" #Enable Big Desktop
Option "Mode2"         "1024x768" #Resolution for second monitor
Option "DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CRT, AUTO
Option "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
Option "HSync2" "65" #This sets the horizontal sync for the secondary display. 31-61
Option "VRefresh2" "60" #This sets the refresh rate of the secondary display. 56-75
EndSection

Section "Monitor"
	Identifier	"P19-1A"
	Option		"DPMS"
	HorizSync	31-64
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X800 (R430 UO)"
	Monitor		"P19-1A"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by CARRnage8473 on 2007-12-23
> **electrofreak66 said:**
> You can choose either. Dual-Head has two distict desktops running. Big Desktop mode lets you share windows amongst the screens. This sounds like it is what you want. To do that type:
```
sudo aticonfig --dtop=horizontal --overlay-on=1
```

This is exactly what I needed to get mine working.  Thank you very much.

---

