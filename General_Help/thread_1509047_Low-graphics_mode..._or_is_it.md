---
title: "Low-graphics mode... or is it?"
date: 2010-06-13
forum: General Help
---

### Post by intheflesh on 2010-06-13
Hi all. I've been using Ubuntu for about six months now in continuity (I also tried 5.10 back then, but not for long) and I must admit it has given me quite some trouble. It was 9.04 that I installed and decided to make a dual boot with WinXP (I'm happy to inform you I've been 'sober' for two and a half months - haven't booted Windows since March :)).

It appears that every bug that could occur when upgrading - happened to me. First it was that blank screen upon booting (which I solved by removing fglrx driver and reconfiguring X) when I upgraded to 9.10, then gdm, continually showing up after logging in and just before GNOME initializing (which I "solved" by removing compiz and reinstalling it (a couple of times...) Now there's this new bug in a form of a peculiar dialog showing up instead of gdm, stating my computer is running in low graphics mode.

The problem occurred today. I was running 10.04 for about a month and everything ran smoothly (almost... but that's another story). Update manager kept complaining about packages not being installed and offered me a partial upgrade which I completed on a warm night just when my neighbor, from whom I am "borrowing wireless connection", decided he had enough of watching redtube thus making my DL rate jump to about 107kB/s which was decent enough to do the >500MB downloading. After it installed those updates and I hit restart, I was greeted warmly with before-mentioned message. None of the proposed solutions the dialog was offering helped (nor they did anything, for that matter...) Restoring my original xorg.conf didn't help too, so I referred to the 'hacks' I used to fix my earlier problems. Since you're reading this, you are guessing correctly that I failed.
After hacking some more, I found out I could go to recovery mode, fire up root console, login as a user and startx - and everything would worke just like before update! Weird, huh? When I boot normally, Ubuntu says it cannot recognize my graphic card, sound card, etc. But when I login 'the hard' way - everything works just like before. Just for a kinda noobish benchmark, I ran glxgears and got 662.28 fps (average five cycles), which is OK (I think) for my specs.

So, my question is: what the **** is going on?! And how do I fix it? I do mind having to go to all this hassle just to login... If it's some new kind of service checking that 'things are working' - how do I shut it down? If it's a driver issue - how do I fix that?



Hardware specs:
CPU: Intel Celeron 4 GHz Prescott core (this much I know)
MOBO: ASRock P4i65G
Memory: Samsung 512MB PC3200
AUdio: Onboard AC97
Graphics: Ati Radeon 9800Pro 128MB (the man who sold me this machine say it's actually a [soft]modded SE version...)
HDD: Hitachi 250GB and an old (almost malfunctioning - drops to PIO in Windows, runs okay in Ubuntu) 80GB Maxtor (did they make ANY good harddisks?! I myself broke three out of three I owned...)

dmesg | grep drm output, in case anyone's interested:
```
[    0.000000] Linux version 2.6.32-22-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
[   16.038904] [drm] Initialized drm 1.1.0 20060810
[   16.893842] [drm] radeon defaulting to kernel modesetting.
[   16.893849] [drm] radeon kernel modesetting enabled.
[   16.904998] [drm] radeon: Initializing kernel modesetting.
[   16.910495] [drm] register mmio base: 0xFF0F0000
[   16.910500] [drm] register mmio size: 65536
[   16.913275] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   16.920725] [drm] Generation 1 PCI interface in multifunction mode
[   16.920732] [drm] Limiting VRAM to one aperture
[   16.920830] [drm] radeon: VRAM 128M
[   16.920833] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   16.920835] [drm] radeon: GTT 32M
[   16.920838] [drm] radeon: GTT from 0xFC000000 to 0xFDFFFFFF
[   16.920869] [drm] radeon: irq initialized.
[   16.921004] [drm] Detected VRAM RAM=128M, BAR=128M
[   16.921010] [drm] RAM width 256bits DDR
[   16.929098] [drm] radeon: 128M of VRAM memory ready
[   16.929102] [drm] radeon: 32M of GTT memory ready.
[   16.929345] [drm] radeon: 2 quad pipes, 1 Z pipes initialized.
[   16.929359] [drm] radeon: cp idle (0x10000C00)
[   16.929530] [drm] Loading R300 Microcode
[   16.987743] [drm] radeon: ring at 0x00000000FC000000
[   16.987768] [drm] ring test succeeded in 1 usecs
[   16.998934] [drm] radeon: ib pool ready.
[   16.999039] [drm] ib test succeeded in 0 usecs
[   17.000963] [drm] Default TV standard: NTSC
[   17.000969] [drm] 27.000000000 MHz TV ref clk
[   17.000975] [drm] DFP table revision: 4
[   17.002679] [drm] Default TV standard: NTSC
[   17.002684] [drm] 27.000000000 MHz TV ref clk
[   17.002976] [drm] Radeon Display Connectors
[   17.002980] [drm] Connector 0:
[   17.002983] [drm]   VGA
[   17.002986] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   17.002988] [drm]   Encoders:
[   17.002990] [drm]     CRT1: INTERNAL_DAC1
[   17.002992] [drm] Connector 1:
[   17.002993] [drm]   DVI-I
[   17.002995] [drm]   HPD1
[   17.002998] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   17.002999] [drm]   Encoders:
[   17.003001] [drm]     CRT2: INTERNAL_DAC2
[   17.003003] [drm]     DFP1: INTERNAL_TMDS1
[   17.003005] [drm] Connector 2:
[   17.003007] [drm]   S-video
[   17.003009] [drm]   Encoders:
[   17.003010] [drm]     TV1: INTERNAL_DAC2
[   17.329316] [drm] fb mappable at 0xF0040000
[   17.329321] [drm] vram apper at 0xF0000000
[   17.329323] [drm] size 5242880
[   17.329325] [drm] fb depth is 24
[   17.329327] [drm]    pitch is 5120
[   17.341661] fb0: radeondrmfb frame buffer device
[   17.341678] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0

```

[SIZE=5][COLOR=Red]**EDIT:**[/COLOR][/SIZE]
[SIZE=3]The issue is now solved, thank to a couple of new updates and, most importantly, installation of gdm which has been lost tanks to one of my attempts to make it work. Thank you all for your help![/SIZE]

---

### Post by medic2000 on 2010-06-13
Ati cards are pain in the ***. I suggest remove everything about the driver and install again. Be careful to install only one(proprietary or free software driver).

---

### Post by intheflesh on 2010-06-13
Yeah, I'm thinking about it now. I'm thinking of trying the propritary driver now. Since I cannot connect to the intternet in console (it works from panel...), can I just ```
sudo apt-get remove xserver-xorg-video-ati
```, then follow the instructions from [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), log out and log in and it works? I mean, do I have to restart after I remove free drivers?

---

### Post by clhsharky on 2010-06-13
intheflesh

> I'm thinking of trying the propritary driver now

Ati Radeon 9800Pro 128MB  card is legacy for fglrx since catalyst9.3 on ubuntu8.10. A latter catalyst will not work on your card.

Radeon is the correct driver for your card on ubuntu9.04 to present.

There are fresher radeon drivers and kernels that may help with performance and features.

Sharky

---

### Post by intheflesh on 2010-06-13
Thanks for the information.
So, no priprietary drivers then. I doubt that installing pre 9.3 version of catalyst drivers would work on 10.04...

What can I do then? If I can manually start X with no problems, why wouldn't Ubuntu do that on it's own?

---

### Post by clhsharky on 2010-06-13
intheflesh

How did you upgrade and what is in your /etc/X11/xorg.conf file.

Lucid doesn't have xorg.conf by default.

Sharky

---

### Post by intheflesh on 2010-06-14
I downloaded the CD via torrent, mounted it and ran
```
gksu "sh /cdrom/cdromupgrade"
```
as stated on the wiki page.
Update manager downloaded the rest of the packages. Since my connection breaks often, I did the downloading in parts. After that, update manager informed me that there were updates available, >500MB's of them, so I downloaded them in parts as well. When it was finally over (a couple of weeks later), I got that low-graphics message upon booting.

Here's my current xorg.conf:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "record"
	Load  "extmod"
	Load  "dbe"
	Load  "dri2"
	Load  "glx"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  340   270	# mm
	Identifier   "Monitor0"
	VendorName   "MAX"
	ModelName    "Belinea"
	HorizSync    31.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPFastWrite"       	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "FBTexPercent"       	# <i>
        #Option     "DepthBits"          	# <i>
        #Option     "PCIAPERSize"        	# <i>
        #Option     "AccelDFS"           	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "CustomEDID"         	# [<str>]
        #Option     "DisplayPriority"    	# [<str>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForceMinDotClock"   	# <freq>
        #Option     "ColorTiling"        	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "RageTheatreCrystal" 	# <i>
        #Option     "RageTheatreTunerPort" 	# <i>
        #Option     "RageTheatreCompositePort" 	# <i>
        #Option     "RageTheatreSVideoPort" 	# <i>
        #Option     "TunerType"          	# <i>
        #Option     "RageTheatreMicrocPath" 	# <str>
        #Option     "RageTheatreMicrocType" 	# <str>
        #Option     "ScalerWidth"        	# <i>
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "SubPixelOrder"      	# [<str>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "ClockGating"        	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
        #Option     "ReverseDDC"         	# [<bool>]
        #Option     "LVDSProbePLL"       	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ConnectorTable"     	# <str>
        #Option     "DefaultConnectorTable" 	# [<bool>]
        #Option     "DefaultTMDSPLL"     	# [<bool>]
        #Option     "TVDACLoadDetect"    	# [<bool>]
        #Option     "ForceTVOut"         	# [<bool>]
        #Option     "TVStandard"         	# <str>
        #Option     "IgnoreLidStatus"    	# [<bool>]
        #Option     "DefaultTVDACAdj"    	# [<bool>]
        #Option     "Int10"              	# [<bool>]
        #Option     "EXAVSync"           	# [<bool>]
        #Option     "ATOMTVOut"          	# [<bool>]
        #Option     "R4xxATOM"           	# [<bool>]
        #Option     "ForceLowPowerMode"  	# [<bool>]
        #Option     "DynamicPM"          	# [<bool>]
        #Option     "NewPLL"             	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
	Option 		"EnableDepthMoves"			"True"
	Option		"EnablePageFlip"			"True"
	Option		"DMAForXv"					"True"
	Option		"AccelDFS"					"True"
	Option		"ColorTiling"				"True"
	Option		"RenderAccel"				"True"
	Option		"VGAAccess"					"True"
	Option		"AccelMethod"				"EXA"
	Option		"DRI"						"True"
	Option		"MigrationHeuristics"		"greedy"
	Option		"TripleBuffer"				"True"
	Option		"EXAOptimizeMigration"		"True"
	Option		"EXANoComposite"			"No"
	Option		"BackingStore"				"True"
	Option		"AGPMode"					"8"
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon R350 [Radeon 9800 Pro]"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option		"RENDER"		"Enable"
	Option		"Composite"		"True"
	Option		"XVideo"		"Enable"
	Option		"XINERAMA"		"False"
EndSection

Section "DRI"
	Mode		0666
EndSection
```

---

### Post by eggdeng on 2010-06-14
I think this is the KMS problem described in the link in my sig. I was able to solve it by creating a file /etc/modprobe.d/radeon-kms.conf which contains the single line
```
options radeon modeset = 0
```

---

### Post by intheflesh on 2010-06-15
> **eggdeng said:**
> I think this is the KMS problem described in the link in my sig. I was able to solve it by creating a file /etc/modprobe.d/radeon-kms.conf which contains the single line
```
options radeon modeset = 0
```

Doesn't work. Says ```
[    18.something] radeon: `' invalid for parameter `modeset'
```

---

### Post by eggdeng on 2010-06-15
There is an alternative on this page [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes") Just search for KMS.

---

### Post by intheflesh on 2010-06-17
This is getting really depressing...

Added ```
kopt=nomodeset
``` just above kernel listings and all, still the problem persists. Guess I didn't do it right. Here's the listing of /boot/grub/menu.lst:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		11

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fc48ece9-a490-4950-ba02-d49a9635ccc9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fc48ece9-a490-4950-ba02-d49a9635ccc9

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##
#
# Dodao nomodeset...
kopt=nomodeset
# Ostalo nisam dirao...
#

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		fc48ece9-a490-4950-ba02-d49a9635ccc9
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=fc48ece9-a490-4950-ba02-d49a9635ccc9 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		fc48ece9-a490-4950-ba02-d49a9635ccc9
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=fc48ece9-a490-4950-ba02-d49a9635ccc9 ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		fc48ece9-a490-4950-ba02-d49a9635ccc9
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=fc48ece9-a490-4950-ba02-d49a9635ccc9 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		fc48ece9-a490-4950-ba02-d49a9635ccc9
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=fc48ece9-a490-4950-ba02-d49a9635ccc9 ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid		fc48ece9-a490-4950-ba02-d49a9635ccc9
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=fc48ece9-a490-4950-ba02-d49a9635ccc9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid		fc48ece9-a490-4950-ba02-d49a9635ccc9
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=fc48ece9-a490-4950-ba02-d49a9635ccc9 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
uuid		fc48ece9-a490-4950-ba02-d49a9635ccc9
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=fc48ece9-a490-4950-ba02-d49a9635ccc9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
uuid		fc48ece9-a490-4950-ba02-d49a9635ccc9
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=fc48ece9-a490-4950-ba02-d49a9635ccc9 ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-11-generic
uuid		fc48ece9-a490-4950-ba02-d49a9635ccc9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=fc48ece9-a490-4950-ba02-d49a9635ccc9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid		fc48ece9-a490-4950-ba02-d49a9635ccc9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=fc48ece9-a490-4950-ba02-d49a9635ccc9 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		fc48ece9-a490-4950-ba02-d49a9635ccc9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


```

Tried to add a nomodeset option in the grub boot menu (_e_dited, then _o_pened a new line before quiet and typed nomodeset) but when I tried to _b_oot, system rebooted...

Also, a new message appeared below the information that I'm running low-graphics mode, it says something about Radeon failed GetVersion or something... I'll write it down next time.

I uninstalled and reinstalled free ati driver. I guess it made things worse...

Also, I just realized, when I go to System - Preferences - Monitors, it doesn't display my monitor's real name (Belinea), but "Rogen Tech Distribution" instead.

I'm getting pretty suicidal here...

EDIT:
The message now says:
```
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
```
I learned thet "quiet splash" and "nomodeset" should not go together, so I will try with just "nomodeset".

---

### Post by intheflesh on 2010-06-17
Replacing "quiet" with "nomodeset" in boot splash doesn't work. I'm out of ideas. Will try adding nomodeset in menu.lst instead.

---

### Post by intheflesh on 2010-06-17
Ok, deliberately bumping, but I've tried everything and nothing works. I don't know what is going on. Starting x manually from console doesn't seem to work smoothly, yet I'm being warned at startup that Ubuntu cannot recongnize my graphic card? It's idiotic... drm loads, radeon driver loads, no errors whatsoever, yet, still that screen appears...

Can someone at least explain what are common causes of the low-graphics mode warning?

---

