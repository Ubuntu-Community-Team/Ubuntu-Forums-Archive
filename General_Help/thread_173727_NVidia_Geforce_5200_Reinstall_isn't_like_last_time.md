---
title: "NVidia Geforce 5200 Reinstall isn't like last time"
date: 2006-05-10
forum: General Help
---

### Post by tamarku on 2006-05-10
OK, I was interested in KDE.  I downloaded it and it was all mixed up with my gnome icons and everything was messy.  SO, I played with SimplyMepis for a bit and didn't like it.  Now I am back to Ubuntu, running gnome, ran automatix.  Now when I run glxgears and let it run for about half an hour no fps show up.  My GL screensavers seem to work ok, of course any websites with flash don't work anyway so I can't tell about videos.  I do have some videos from friends emails and they seem to work.  How do I know if I have 3d acceleration working?  How do I know if I have the drivers setup.  I see the flash, I see the Nvidia desktop.settings.  I have GLCore and dri commented out.  Can anyone help me figure out if I have the video set up correctly?  I'm running an NVidia Geforce FX 5200 w/ 128mb, AMD Sempron 1.3 Processor, 768mb of RAM.  If you need any more system info let me know how to get.  By the way, I'm liking Ubuntu/Linux so much I have gone to straight Ubuntu on my machine.  So slowly I will be trying to get my printer, scanner and everything working.  

As always, any and all help will be greatly appreciated.

---

### Post by Omnios on 2006-05-10
I have the same problems with Glxgears but needless to say my glx is owrking rather well and games are ok. I think they did some changes with glxears when Breezy came out.

---

### Post by astoltz on 2006-05-10
To get glxgears to show the frame rate: ```
glxgears -printfps
```

---

### Post by Sutekh on 2006-05-10
Use
```
glxgears -iacknowledgethatthistoolisnotabenchmark
```

---

### Post by tamarku on 2006-05-10
Okay, now I'm pretty sure I don't have it installed correctly.  I'm only getting 889 to 881 fps???? The first time I installed I was able to get this up to almost 1700 fps.  Anyone know why I've done wrong??  Or where do I start to try to fix this?? I've looked at threads and when I've tried them I'm I have the newest version of the packages.

---

### Post by Omnios on 2006-05-10
Getting about 1100 with a Gforce MX4

---

### Post by Sutekh on 2006-05-10
Check that your CPU speed has not been dialled back by the PowerNow daemon
```
cat /proc/cpuinfo
```

Also is the glxgears window larger?  Are you running other processes?  

Remember its not a realiable benchmark, still I would have thought you'd be a little closer.

---

### Post by Omnios on 2006-05-10
See what you get with these commands.
```


lsmod |grep -i agp

cat /proc/driver/nvidia/agp/status

cat /proc/driver/nvidia/cards/0


```

 This will give you info on your vid card and tell whats doing what.

---

### Post by tamarku on 2006-05-10
I realize this isn't a benchmark but I would have thought this would be over 1000 fps??

OK, here is what cat /proc/cpuinfo got me: 

kaos@wintergreen:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 8
model name      : AMD Sempron(tm)   2400+
stepping        : 1
cpu MHz         : 1662.783
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow
bogomips        : 3301.37


And now for the other commands: 

kaos@wintergreen:~$ lsmod |grep -i agp
sis_agp                 8452  1
agpgart                32328  2 sis_agp,nvidia
kaos@wintergreen:~$


kaos@wintergreen:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled


kaos@wintergreen:~$ cat /proc/driver/nvidia/cards/0
Model:           GeForce FX 5200
IRQ:             16
Video BIOS:      04.34.20.67.00
Card Type:       AGP


There you have it.  It looks to me like everything is id'd correctly.  But, I have to admit, I'm NOT techie enough to know what any of this means.

---

### Post by Omnios on 2006-05-10
> kaos@wintergreen:~$ cat /proc/driver/nvidia/agp/status
Status: Enabled
Driver: AGPGART
AGP Rate: 8x
Fast Writes: Disabled
SBA: Enabled
 
 This is a problem right here it should be nvidia. Here is mine.
```

```tom@reboot:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled
tom@reboot:~$

 Also I have.
[CODE][tom@reboot:~$ lsmod |grep -i agp
agpgart                34792  1 nvidia
/CODE]


 If I remember you have to black list agp,gart. One sec let me look it up.

---

### Post by tamarku on 2006-05-10
That would makes sense that that is wrong.  Yep, I have no idea what I would need to do to disable the AGPGART. And change my driver to NVIDIA instead of the AGP.

---

### Post by Omnios on 2006-05-10
This is a post from my old nvidia card pertaining to agp. I used it as a reference t for my current set up.
[http://ubuntuforums.org/showthread.php?t=44871&highlight=nvidia]("http://ubuntuforums.org/showthread.php?t=44871&highlight=nvidia")

---

### Post by tamarku on 2006-05-10
Well, I blacklisted just the intel-agp.  Then added those options to my xorg.conf and that blew up my Xwindow.  When I tried to reboot I got a blue screen.  I was able to restore my backup so I'm up again.  BUT, that didn't work.  I'm still using the AGPGART.

---

### Post by ZylGadis on 2006-05-10
I don't think the AGPGART is guilty. I apparently use it (I installed the ubuntu nvidia drivers), and my FX5200 gives me 1400+ FPS. My cpu is a little lower than yours, and the AGP is 4x, so not reaching 1700 makes sense.

> cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled


I have no idea what SBA is, but mine and Omnios's are disabled and our cards are fine, while yours is enabled and your card is not ok. Maybe you should look into that.

---

### Post by tseliot on 2006-05-11
there's no need to use nvagp instead of AGPGART.

Try this guide of mine and enable AGP Fastwrites:
[http://www.ubuntuforums.org/showthread.php?t=140989]("http://www.ubuntuforums.org/showthread.php?t=140989")

---

### Post by Omnios on 2006-05-11
Hi hi K The only mod I have with the Gforce MX4 is that I black listed the agp gart
```
# AGP Blacklist
agpgart
intel-agp

```
 Some of the nvidia setting in xorg.conf are know to potentualy lock up your xorg. 

 Anyways the intel agp is specific to what hardware you have and I noticed you have sis. Lastly as stated there is no need for this but for me it iliminated screen tearing, the black lines when you move a window around and now my windows are seemless. As for tseliot fastwrite guide, this looks real interesting and im looking into it as it may even increase my agp performance.

---

### Post by tamarku on 2006-05-11
Well I followed your link and here is what I got.  I did get about 100 fps more then before but still waaaaaay lower then when I originally installed Ubuntu and used Automatix to install the NVidia Drivers.  I'm posting all my information for you all too see.  I did notice that FastWrites is still disabled.  All of this by the way is after a Restart.  

kaos@wintergreen:~$ !65
cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled
kaos@wintergreen:~$ !63
glxgears -printfps
4600 frames in 5.0 seconds = 919.890 FPS
4571 frames in 5.0 seconds = 914.156 FPS
4536 frames in 5.0 seconds = 907.076 FPS
4596 frames in 5.0 seconds = 919.135 FPS
4556 frames in 5.0 seconds = 911.126 FPS
4588 frames in 5.0 seconds = 917.497 FPS
4586 frames in 5.0 seconds = 917.082 FPS
4609 frames in 5.0 seconds = 921.777 FPS
4554 frames in 5.0 seconds = 910.766 FPS


Here is my xorg.conf:

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
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


Now here is my nvidia-kernel-nkc file: 

alias char-major-195* nvidia
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1


Also, I had blacklisted intel-agp.  I removed that from the hotplug blacklist.  
So if anyone could help that would be tremendous.

---

### Post by tamarku on 2006-05-12
OK, I followed tseliot's method on installing the Latest NVIDIA drivers.  It all seemed to go smooth.  However I am still about 919 fps on glxgears, I realize this isn't a benchmark, and when I minimize any window I see the black lines on the screen.  I can't seem to get fastwrites enabled, SBA is enable.  I'm going to search on that for now and see if I can get that enabled.  

I don't know if anyone is checking in on this thread anymore but thanks for the responses and the help that everyone gave me.

---

