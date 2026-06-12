---
title: "Hoary - Xorg - take up lot of CPU resources"
date: 2005-03-05
forum: General Help
---

### Post by JGJones on 2005-03-05
PC - P3 800MHz with 256Mb and Nvidia GeForce FX5200 (128Mbb)

I had Warty with XFree86 -  nvidia driver was installed from apt-get successful, OpenGL applications worked fine.

Move a window in xGnome however take up to 70% CPU resources

As a result Gnome isn't fun to use, you can see windows being redrawn etc (I have 2nd PC with Windows XP) and I wanted to use Ubuntu as my work machine, but I keep going back to Windows since it does have a much more snappy feel to the GUI!

Later on I have updated my Ubuntu system to the Hoary (change Warty to Hoary in res in Synaptic Package Manager) and updated everything using Smart update. and rebooted.

Then I installed xorg and  uninstalled XFree86 and rebooted - I am now running Ubuntu Hoary with xorg and the Nvidia driver is running fine without needing to configy the xorg.conf file.

OpenGL applications still fine.

Move a window in Gnome still suck up 70% CPU and so it slows down the whole system to the point that it's just silly.

In Windows you can have the card render the windows and so on - which gives it a very snappy fieel.

Can you do the same thing in Xorg so that the card is doing the work NOT the CPU?? If so, how do I do that? And don't someone dare tell me to read the readme file from nvidia - this I have done and it does not help an iota.

This problem of xorg/xfree taking up large amount of CPU is ruining what is a otherwise   fantastic Linux distro and from reading in here it seem I'm not isolated If someone have a solution, please post and it should be made sticky :)

Cheers

---

### Post by Biffy on 2005-03-05
I seem to have the same problems. I installed the Nvidia drivers in hoary and OpenGL applications works fine, but simple 2D-games is slow as hell. Even fluxbox is slow.

---

### Post by JGJones on 2005-03-05
I've also asked the same question in the LinuxQuestion forum - which is a fantastic place to ask for help to do with Linux like this forum and so far no-one there seem unable to answer the question above??

Is Linux that flawed? I think not! I know there's a solution, come on someone, help us stop going back to the dreaded Windows cos I'm getting awfully tempted by switching back to Windows!!! :)

Cheers

---

### Post by dwm on 2005-03-06
I am having the same problems. Started happening after a large update around March 1st.

---

### Post by Hikaru79 on 2005-03-06
Yeah... same here =( Incredible slow GUI, much slower than before, even though I'm using the "Simple" theme in GNOME... I'm on NVIDIA. Anything to be done?

---

### Post by JGJones on 2005-03-06
[```
# XF86Config-4 (XFree86 X Window System server configuration file)
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
#	VideoRam	131072

EndSection

Section "Monitor"
	Identifier	"HM903DB/DTB"
	HorizSync	30-132
	VertRefresh	50-200
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"HM903DB/DTB"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
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
``` 

I've tried it with and without VideoRAM (in Kb's) HWCurosr, few dozen other options and none of them make any difference to the GUI

The Theme I use is Clearlook however even the Simple theme does not make any difference it's still taking huge amount of CPU just to do anything to do with X (move window, minimize etc) at idle, CPU is at idle so it's not conitinously using CPU, just when you do work with the GUI

---

### Post by justBE on 2005-03-06
hey there...

same for me -  got a p4 3ghz, 1gig ram, geforce 6800 and hoary up-to-date.. but the gui/x is crawling like hell... (opengl/3d works fine)


:\

---

### Post by daniels on 2005-03-06
Put Option "RenderAccel" (I think) into your Device section, and it should go a lot faster.

---

### Post by Nech on 2005-03-06
[QUOTE=daniels]Put Option "RenderAccel" (I think) into your Device section, and it should go a lot faster.[/QUOTE]

I have the same problem, and this it is not the solution :-( 

I have installed from zero the hoary and have updated of warty to hoary, and in both ways I have had the same problem

*I'm sorry, my English is very bad

---

### Post by p!=f on 2005-03-06
Same here. Over 13% CPU consumption after the first login. As soon as I relogin, Xorg drops to 2,7 at max. I think this is GNOME related because I don't experience this in KDE (yeah, I installed KDE just to see the difference :)) and Waimea.
When you create new user account / recreate new GNOME profile for you it's gone till you tweak your profile a bit. Really annoying.

I use Gorilla theme with Gartoon icons.

(edit: Forgot to add I use nVidia card too)

---

### Post by JGJones on 2005-03-06
[QUOTE=p!=f]Same here. Over 13% CPU consumption after the first login. As soon as I relogin, Xorg drops to 2,7 at max. I think this is GNOME related because I don't experience this in KDE (yeah, I installed KDE just to see the difference :)) and Waimea.
When you create new user account / recreate new GNOME profile for you it's gone till you tweak your profile a bit. Really annoying.

I use Gorilla theme with Gartoon icons.

(edit: Forgot to add I use nVidia card too)[/QUOTE]

I created new account and logged on with that and at once first thing I did was open a terminal window and run the command "top" and then I opened my home folder.

I moved the home folder window around and xorg shot up to 70% and I haven't touched the profile at all, it was the default ubuntu theme.

I had the problem in Warty and so I upgraded to Hoary to see if it'll fix it and sadly no it didn't and now I'm in Hoary running xorg instead of Warty with XFree86. I'm happy with Hoary just a pity I'm getting slow GUI. 

I'll be submitting this as a bug to Ubuntu's bugzilla and hopefully the devs will see it and fix it asap :) I'll point them to this thread as it explain better and show it's not unique problem to one user.

Cheers

---

### Post by justBE on 2005-03-06
can you please post the bug-id# once you posted the bug so we can track it in bugzilla too? :)

---

### Post by JGJones on 2005-03-06
[QUOTE=justBE]can you please post the bug-id# once you posted the bug so we can track it in bugzilla too? :)[/QUOTE]

Sure will do...I just tested it with "nv" only instead of nvidia...still huge CPU suckage and no 3D.

Oh well bug time...ID to follow....

---

### Post by JGJones on 2005-03-06
[QUOTE=JGJones]Sure will do...I just tested it with "nv" only instead of nvidia...still huge CPU suckage and no 3D.

Oh well bug time...ID to follow....[/QUOTE]
 Bug-id# is 7250 - direct link - [https://bugzilla.ubuntu.com/show_bug.cgi?id=7250](https://bugzilla.ubuntu.com/show_bug.cgi?id=7250)

Let's hope it's a quick fix.

---

### Post by daniels on 2005-03-06
It's been suggested that newer kernels show this problem up, and you need to blacklist the agpgart module to fix it.

---

### Post by JGJones on 2005-03-06
[QUOTE=daniels]It's been suggested that newer kernels show this problem up, and you need to blacklist the agpgart module to fix it.[/QUOTE]

Thanks....err...what does that mean in English? :) What do we have to do since what you just said mean...err...bugger all to be frank, sorry :) I'm still a newbie to Linux...learning quickly as Ubuntu is nice, but still a newbie nonetheless.

---

### Post by ubart on 2005-03-07
Hi, this is not a nVidia problem. I have an ATI Radeon 9600 and have the same problem with both the fglrx and the ati drivers.

---

### Post by kahping on 2005-03-07
[QUOTE=Bart Pieterse]Hi, this is not a nVidia problem. I have an ATI Radeon 9600 and have the same problem with both the fglrx and the ati drivers.[/QUOTE]

i agree that this isn't a nVidia problem. i installed warty, upgraded to hoary, then followed the instructions given @ [http://www.ubuntuguide.org](http://www.ubuntuguide.org) on installing nVidia drivers and enabling hardware acceleration, and have not such problems at all.

i can't say that my desktop is silky smooth with the "hardware acceleration" enabled, but neither do i have the super draggy situation described in this thread.

i'm still a newbie to Linux myself, though, so i have no idea what's your problem here. sorry.

kahping

---

### Post by justBE on 2005-03-07
[QUOTE=daniels]It's been suggested that newer kernels show this problem up, and you need to blacklist the agpgart module to fix it.[/QUOTE]


daniel,

how do we blacklist the agpart module and will in terms of the nvidia module, the NVAGP module work/jump in automatically (as long as the corresponding option is set in xorg.conf)?

---

### Post by JGJones on 2005-03-07
[QUOTE=JGJones]Thanks....err...what does that mean in English? :) What do we have to do since what you just said mean...err...bugger all to be frank, sorry :) I'm still a newbie to Linux...learning quickly as Ubuntu is nice, but still a newbie nonetheless.[/QUOTE]

I've disabled the agpgart by adding it to the blacklist so that the NVidia AGP will load up instead - this works, but I am still getting horrible slow GUI despite those changes I've made

(One useful thing about this problem is that it's making me learn about the inner workings of Linux quicker :D)

---

### Post by JGJones on 2005-03-07
[QUOTE=justBE]daniel,

how do we blacklist the agpart module and will in terms of the nvidia module, the NVAGP module work/jump in automatically (as long as the corresponding option is set in xorg.conf)?[/QUOTE]

Thanks to that suggestions I've learnt a wee bit ;)

This is what you need to do to blacklist the agpgart:

go to terminal

```
 lsmod |grep -i agp
```

That will show the AGP modules in use by your system - agpgart followed by the chipset specific module (in my case it is intel-agp as I have intel chipset so I shall use that)

```
 sudo gedit /etc/hotplug/blacklist 
```

Add the two lines as below:

```
 agpgart
 intel-agp
```

If you have sis chipset you would get sis-agp from the earlier command so replace intel-agp with that for example.

```
 sudo gedit /etc/X11/xorg.conf 
```

and edit your Device section so that it includes the two lines as below:

Option "RenderAccel" "true" - as suggested by Daniel
Option	"NvAGP" "1" - enables the NVAGP module if agpgart not present (which is why you need to blacklist it)

```
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	131072
        Option 		"NoLogo" 		"yes"
	Option 		"RenderAccel" 		"true"
	Option 		"NvAGP" 		"1"

EndSection
```

Reboot your computer

When you have logged in, open terminal again and type in the command:

```
 dmesg |grep -i nvidia 
```

if you did the above successful you should get this output:

```
 nvidia: module license 'NVIDIA' taints kernel.
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-6629  Wed Nov  3 13:12:51 PST 2004
```

if not then run the dmesg command again without grep and at end of that long list of text you would get a line saying the NVRM failed to load, AGPGART already loaded! - this mean it wasn't blacklisted properly - make sure you blacklist your chipset specific agp part as well.

If for some reason blacklisting doesn't work for you, there is a roundabout way - not a recommended way

go to /lib/modules/<your kernel>/kernel/drivers/char/agp and rename agpgart.ko to agpgart.ko.saved

On boot up Linux won't find agpgart.ko and so not load it.

Blacklisting is better since it survivies kernel upgrades.

---

### Post by p!=f on 2005-03-07
[QUOTE=p!=f]Same here. Over 13% CPU consumption after the first login. As soon as I relogin, Xorg drops to 2,7 at max. I think this is GNOME related because I don't experience this in KDE (yeah, I installed KDE just to see the difference :)) and Waimea.
When you create new user account / recreate new GNOME profile for you it's gone till you tweak your profile a bit. Really annoying.

I use Gorilla theme with Gartoon icons.

(edit: Forgot to add I use nVidia card too)[/QUOTE]
So I continued in my hunt for this issue:
1) I created new user account without any changes made to the theme / GNOME environment
2) I restarted the computer, login, ran gnome-terminal, top and voila xorg usage is over 9%.
3) I relogin with this account, ran gnome-terminal, top and voila xorg usage is under or slightly around 3%.

Tested kernels:
2.6.10-4-k7 with agpgart and via_agp blacklisted
2.6.11-cko1 with agpgart module disabled in the kernel

xorg.conf:
```

[~] > cat /etc/X11/xorg.conf
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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/Speedo"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "fb"
        Load    "fbdev"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "speedo"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
        Load    "xtt"
EndSection

Section "Extensions"
#       Option  "Composite"     "Enable"
        Option  "RENDER"        "Enable"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xfree86"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV34 [GeForce FX5200]"
        Driver          "nvidia"
        #Driver         "nv"
        Option          "NvAGP" "1"
        #Option         "AllowGLXWithComposite" "1"
        Option          "NoLogo" "0"
        Option          "RenderAccel" "1"
        Option          "HWCursor" "1"
        Option          "CursorShadow" "1"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "AOC HT731"
        HorizSync       30-95
        VertRefresh     50-160
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV34 [GeForce FX5200]"
        Monitor         "AOC HT731"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

lspci output:
```

[~] > lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0269
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1269
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2269
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3269
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4269
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7269
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0b.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

Adding some screen from my own account so you can see it all ;)

Could anyone give it a try before I post a bug?

(edit: I forgot to mention I did not move a single window)

---

### Post by JGJones on 2005-03-07
Just scrolling down this forum which is mainly text give me this from top:

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5938 root      16   0  184m  37m 6892 R 78.1 14.9  19:03.62 Xorg
 7283 jgjones   16   0  124m  44m  16m S 18.9 17.6   7:15.80 firefox-bin
10363 jgjones   15   0 97332  32m  15m S  1.3 12.9   3:04.47 nvu-bin

```

As you can see, xorg is taking up 78.1 CPU resources JUST to scroll down a webpage (I was going farily quickly down mind you but even that shouldn't take up so much CPU should it?)

As for my xorg.conf file, here it is:

```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
#	VideoRam	131072
        Option 		"NoLogo" 		"1"
	Option 		"RenderAccel" 		"1"
	Option 		"NvAGP" 		"1"
#	Option		"AllowGLXWithComposite" "1"
        Option		"HWCursor" "1"

EndSection

Section "Monitor"
	Identifier	"HM903DB/DTB"
	HorizSync	30-132
	VertRefresh	50-200
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"HM903DB/DTB"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

```

and my lspci give me:

```

0000:00:00.0 Host bridge: Intel Corp. 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82815 815 Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801AA USB (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801AA AC'97 Audio (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
0000:02:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
0000:02:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

```

And to verifies that 3D does indeed works on my system, here's the output from glxgears:

```

jgjones@hobbit:/lib/modules $ glxgears
3031 frames in 5.0 seconds = 606.200 FPS
3481 frames in 5.0 seconds = 696.200 FPS
3475 frames in 5.0 seconds = 695.000 FPS
3479 frames in 5.0 seconds = 695.800 FPS
3477 frames in 5.0 seconds = 695.400 FPS

```

The problem is that xorg isn't very smooth, it feels more like I'm working on a P2 400MHz laptop with 64Mb running NeoMagic graphics...wait I have one of that! a Sony! Yep my P3 800MHz with 256Mb's x-server behaves the same as it does on the laptop - suck up resources and isn't smooth as you would expect coming from Windows :)

---

### Post by Biffy on 2005-03-07
I have a computer here with Ubuntu hoary and fglrx drivers. Things works very good on this machine.

On my other machine, with nvidia drivers, i have serious problems with 2D-applications as all of you have.

So, are you guys sure this isnt a nvidia problem? Cause i think it is.

---

### Post by ubart on 2005-03-07
Hi I have just found something on the mailinglist that seems to solve the problem on my (ATI) system. The CPU frequency scaling seems to be to agressive. See this bug:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=7259](https://bugzilla.ubuntu.com/show_bug.cgi?id=7259)

If I kill powernowd my problems are gone :)

Hope this helps


[QUOTE=Biffy]I have a computer here with Ubuntu hoary and fglrx drivers. Things works very good on this machine.

On my other machine, with nvidia drivers, i have serious problems with 2D-applications as all of you have.

So, are you guys sure this isnt a nvidia problem? Cause i think it is.[/QUOTE]

---

### Post by Biffy on 2005-03-07
No, turning of powernowd didnt help on my system. :(

---

### Post by Biffy on 2005-03-08
Hello? Where did everyone go? Did turning off powernowd help for all of you? Cause it didnt help at all here.

---

### Post by kiddo on 2005-03-08
I don't know if I'm the only one (it seems so), but mine got fixed today by upgrading: [http://www.ubuntuforums.org/showthread.php?t=18720]("http://www.ubuntuforums.org/showthread.php?t=18720")

Notes:
[list]
[*]didn't touch powernowd   
[*]didn't use renderaccel   
[*]didn't do anything at all except using xorg and my 66.29 nvidia driver o_o 
[/list]

---

### Post by Biffy on 2005-03-09
I just upgraded but still the same problem. I dont know if it's the same error as you guys have tough. I havent noticed any slowness in my system, just my 2D-games that are slow. For example, i get 8 fps in the game barrage. bugsquish is slower than my grandma and so on.

But, 3D-accelerated games (like tuxracer and chromium) works very good.

Yes, this i weird. Simple 2D-games is slow, when advanced 3D-games are fast. Here's my xorg.conf, sorry if its long:

```

# File generated by xorgconfig.

#
# Copyright 2004 The X.Org Foundation
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# The X.Org Foundation BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of The X.Org Foundation shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from
# The X.Org Foundation.
#

# **********************************************************************
# Refer to the xorg.conf(5x) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the font modules
    Load        "type1"
#    Load        "speedo"
    Load        "freetype"
#    Load        "xtt"

# This loads the GLX module
    Load       "glx"
# This loads the DRI module
#    Load       "dri"

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# 

    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/TTF/"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/CID/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/TrueType/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/freefont/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><Fn> VT switch sequence
# (where n is 1 through 12).  This allows clients to receive these key
# events.

#    Option "DontVTSwitch"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"

# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option     "Protocol"      "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option	"Xleds"      "1 2 3"

#    Option "LeftAlt"     "Meta"
#    Option "RightAlt"    "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"    "pc105"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"    "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"   "de"
# or:
#    Option "XkbLayout"   "de"
#    Option "XkbVariant"  "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions"  "ctrl:swapcaps"

# These are the default XKB settings for Xorg
#    Option "XkbRules"    "xorg"
#    Option "XkbModel"    "pc105"
#    Option "XkbLayout"   "us"
#    Option "XkbVariant"  ""
#    Option "XkbOptions"  ""

#    Option "XkbDisable"

    Option "XkbRules"	"xorg"
    Option "XkbModel"	"pc101"
    Option "XkbLayout"	"se"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver	"mouse"
    Option "Protocol"    "PS/2"
    Option "Device"      "/dev/input/mice"

# Mouse-speed setting for PS/2 mouse.

#    Option "Resolution"	"256"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"	"Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"	"9600"
#    Option "SampleRate"	"150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the xorg.conf man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"        "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"        "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"        "/dev/ttyS0"
#    Option     "MinX"          "1412"
#    Option     "MaxX"          "15184"
#    Option     "MinY"          "15372"
#    Option     "MaxY"          "1230"
#    Option     "ScreenNumber"  "0"
#    Option     "ReportingMode" "Scaled"
#    Option     "ButtonNumber"  "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"        "/dev/ttyS0"
#    Option     "MinX"          "231"
#    Option     "MaxX"          "3868"
#    Option     "MinY"          "3858"
#    Option     "MaxY"          "272"
#    Option     "ScreenNumber"  "0"
#    Option     "ReportingMode" "Scaled"
#    Option     "ButtonThreshold"       "17"
#    Option     "ButtonNumber"  "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"

    Identifier  "My Monitor"

# HorizSync is in kHz unless units are specified.
# HorizSync may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

    HorizSync   31.5, 60.0

#    HorizSync	30-64         # multisync
#    HorizSync	31.5, 35.2    # multiple fixed sync frequencies
#    HorizSync	15-25, 30-50  # multiple ranges of sync frequencies

# VertRefresh is in Hz unless units are specified.
# VertRefresh may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

    VertRefresh 50-75

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier	"Standard VGA"
    VendorName	"Unknown"
    BoardName	"Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset	"generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver     "nvidia"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# intalled.

#    BusID      "PCI:0:10:0"

#    VideoRam	256

#    Clocks	25.2 28.3

EndSection

# Device configured by xorgconfig:

Section "Device"
    Identifier  "My Video Card"
    Driver      "nvidia"
	# unsupported card
    #VideoRam    65536
    # Insert Clocks lines here if appropriate
EndSection


# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen 1"
    Device      "My Video Card"
    Monitor     "My Monitor"
    DefaultDepth 24

    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1024x768" "800x600" 
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Simple Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.  In this example, screen 2 is located to the
# right of screen 1.

    Screen "Screen 1"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

# Section "DRI"
#    Mode 0666
# EndSection
```

---

### Post by Biffy on 2005-03-09
Problem solved! I had to change the default depth to 16 instead of 24.

---

### Post by p!=f on 2005-03-09
My problem is gone after HAL upgrade. Kudos devs!

---

### Post by dermotti on 2005-03-09
Powernowd was my issue. Turned it off adn im all good

---

### Post by JGJones on 2005-03-09
Glad it's getting resolved for you guys...sadly I'm still affected by the slow GUI.

Powernowd isn't installed on my system - thus not running.
I'm using Hoary - fully updated to the point that there's no updates pending

I've rebooted ubuntu a couple of time and run dpkg-reconfigure xserver-xorg as well as manually editing the xorg file myself

On a freshly booted Ubuntu, I then open Terminal and then run top. I then maximise the terminal window and leave it as it is, nothing more.

xorg is using up between 15-20% CPU resources just to refresh the terminal window - and I've changed my depth bits from 24 to 16 - no difference.

Do anyone else still have the slow GUI issues as I do? Or am I alone here? :(

Here's a copy of my xorg.conf file - for those with working GUI please post your xorg files in here and confirm that xorg isn't using a large amount of CPU (open terminal, type top and move a window around and see how much CPU resources xorg is using up).

```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbVariant"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"false"
EndSection

Section "Monitor"
	Identifier	"HM903DB/DTB"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"HM903DB/DTB"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
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

```

Still kudos to the dev's for working on this problem, thanks guys :)

---

### Post by JGJones on 2005-03-09
Copy of my xorg log - can't see anything wrong but then I'm not very knowledgable of Linux :) Can anyone see any problem? Thanks

```


X Window System Version 6.8.2 (Ubuntu 6.8.2-2 20050302131250 root@terranova.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 i686 [ELF] 
Current Operating System: Linux hobbit 2.6.10-4-686 #1 Wed Mar 2 06:19:32 UTC 2005 i686
Build Date: 02 March 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-4-686 (buildd@mcmurdo) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Wed Mar 2 06:19:32 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar  9 16:17:51 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "HM903DB/DTB"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc105"
(**) XKB: model: "pc105"
(**) Option "XkbLayout" "gb"
(**) XKB: layout: "gb"
(**) Option "XkbVariant" "gb"
(**) XKB: variant: "gb"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,1130 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1131 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,2418 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2410 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2411 card 8086,2411 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2412 card 8086,2412 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2415 card 0e11,b1bf rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0322 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:09:0: chip 1113,1211 card 1113,1211 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:0a:0: chip 14e4,4320 card 1737,0013 rev 02 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x41000000 - 0x421fffff (0x1200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x48000000 - 0x4fffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[2] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[3] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x40000000 - 0x403fffff (0x400000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0x41000000/24, 0x48000000/27
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0x50000000 from 0x53ffffff to 0x4fffffff
(II) Active PCI resource ranges:
	[0] -1	0	0x40000000 - 0x40001fff (0x2000) MX[B]
	[1] -1	0	0x40100000 - 0x401000ff (0x100) MX[B]
	[2] -1	0	0x50000000 - 0x4fffffff (0x0) MX[B]O
	[3] -1	0	0x48000000 - 0x4fffffff (0x8000000) MX[B](B)
	[4] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[5] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[6] -1	0	0x00002400 - 0x0000243f (0x40) IX[B]
	[7] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[8] -1	0	0x00002440 - 0x0000245f (0x20) IX[B]
	[9] -1	0	0x00002460 - 0x0000246f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x40000000 - 0x40001fff (0x2000) MX[B]
	[1] -1	0	0x40100000 - 0x401000ff (0x100) MX[B]
	[2] -1	0	0x50000000 - 0x4fffffff (0x0) MX[B]O
	[3] -1	0	0x48000000 - 0x4fffffff (0x8000000) MX[B](B)
	[4] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[5] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[6] -1	0	0x00002400 - 0x0000243f (0x40) IX[B]
	[7] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[8] -1	0	0x00002440 - 0x0000245f (0x20) IX[B]
	[9] -1	0	0x00002460 - 0x0000246f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x40000000 - 0x40001fff (0x2000) MX[B]
	[6] -1	0	0x40100000 - 0x401000ff (0x100) MX[B]
	[7] -1	0	0x50000000 - 0x4fffffff (0x0) MX[B]O
	[8] -1	0	0x48000000 - 0x4fffffff (0x8000000) MX[B](B)
	[9] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[13] -1	0	0x00002400 - 0x0000243f (0x40) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00002440 - 0x0000245f (0x20) IX[B]
	[16] -1	0	0x00002460 - 0x0000246f (0x10) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.6629
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.6629
	Module class: XFree86 Video Driver
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) NVIDIA X Driver  1.0-6629  Wed Nov  3 13:14:07 PST 2004
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x40000000 - 0x40001fff (0x2000) MX[B]
	[6] -1	0	0x40100000 - 0x401000ff (0x100) MX[B]
	[7] -1	0	0x50000000 - 0x4fffffff (0x0) MX[B]O
	[8] -1	0	0x48000000 - 0x4fffffff (0x8000000) MX[B](B)
	[9] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[13] -1	0	0x00002400 - 0x0000243f (0x40) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00002440 - 0x0000245f (0x20) IX[B]
	[16] -1	0	0x00002460 - 0x0000246f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x40000000 - 0x40001fff (0x2000) MX[B]
	[6] -1	0	0x40100000 - 0x401000ff (0x100) MX[B]
	[7] -1	0	0x50000000 - 0x4fffffff (0x0) MX[B]O
	[8] -1	0	0x48000000 - 0x4fffffff (0x8000000) MX[B](B)
	[9] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[16] -1	0	0x00002400 - 0x0000243f (0x40) IX[B]
	[17] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[18] -1	0	0x00002440 - 0x0000245f (0x20) IX[B]
	[19] -1	0	0x00002460 - 0x0000246f (0x10) IX[B]
	[20] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[21] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0x48000000
(--) NVIDIA(0): MMIO registers at 0x41000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce FX 5200
(--) NVIDIA(0): VideoBIOS: 04.34.20.56.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at  8 bpp: 400 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 16 bpp: 400 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 32 bpp: 400 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NVIDIA(0): HM903DB/DTB: Using default hsync range of 30.00-132.00 kHz
(II) NVIDIA(0): HM903DB/DTB: Using default vrefresh range of 50.00-200.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 400.00 MHz
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "1024x768" (height 1536 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1446)
(WW) NVIDIA(0): Not using mode "1024x768" (height 1536 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1446)
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1600x1200": 229.5 MHz, 106.2 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "1600x1200": 202.5 MHz, 93.8 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1600x1200": 189.0 MHz, 87.5 kHz, 70.0 Hz
(**) NVIDIA(0):      Default mode "1600x1200": 175.5 MHz, 81.2 kHz, 65.0 Hz
(**) NVIDIA(0):      Default mode "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1400x1050": 184.0 MHz, 93.9 kHz, 85.3 Hz
(**) NVIDIA(0):      Default mode "1400x1050": 155.8 MHz, 81.5 kHz, 74.8 Hz
(**) NVIDIA(0):      Default mode "1400x1050": 151.0 MHz, 77.0 kHz, 70.0 Hz
(**) NVIDIA(0):      Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1440x900": 108.8 MHz, 56.9 kHz, 60.2 Hz
(**) NVIDIA(0):      Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.0 Hz (I)
(**) NVIDIA(0):      Default mode "960x720": 170.7 MHz, 128.5 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "960x720": 148.5 MHz, 112.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "960x720": 117.0 MHz, 90.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "928x696": 144.0 MHz, 112.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "928x696": 109.2 MHz, 86.4 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "896x672": 130.5 MHz, 106.3 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "960x600": 115.0 MHz, 91.0 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 114.8 MHz, 106.2 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 101.2 MHz, 93.8 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 94.5 MHz, 87.5 kHz, 70.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "700x525": 92.0 MHz, 93.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 78.8 MHz, 91.1 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 74.2 MHz, 85.9 kHz, 85.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.9 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): Display dimensions: (370, 270) mm
(--) NVIDIA(0): DPI set to (109, 112)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x48000000 - 0x4fffffff (0x8000000) MX[B]
	[1] 0	0	0x41000000 - 0x41ffffff (0x1000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0x40000000 - 0x40001fff (0x2000) MX[B]
	[8] -1	0	0x40100000 - 0x401000ff (0x100) MX[B]
	[9] -1	0	0x50000000 - 0x4fffffff (0x0) MX[B]O
	[10] -1	0	0x48000000 - 0x4fffffff (0x8000000) MX[B](B)
	[11] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[18] -1	0	0x00002400 - 0x0000243f (0x40) IX[B]
	[19] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[20] -1	0	0x00002440 - 0x0000245f (0x20) IX[B]
	[21] -1	0	0x00002460 - 0x0000246f (0x10) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "UseFBDev" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "XkbVariant" "gb"
(**) Generic Keyboard: XkbVariant: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!
(II) NVIDIA(0): Setting mode "1600x1200"

```

---

### Post by nojjy on 2005-03-09
I'm also having the exact same slowdown problems, even with powernowd uninstalled.  Help us!

---

### Post by daniels on 2005-03-10
It seems there are a few issues here which are all getting lumped into one (rather confusingly).

One: powernowd was briefly doing clock (but not frequency) scaling for P4s, laptop or desktop.  This apparently provided absolutely no benefit on laptops (same power draw), and just made people's desktops run at 425MHz and stuff for no reason, which slowed stuff down badly.  powernowd was updated to fix this a few days ago, so scratch this off the list.

Two: xorg slowdowns.  I'm not entirely convinced that this issue actually exists -- I believe it's almost entirely #1 showing up, and just showing up with Render-intensive stuff because, well, it's pretty slow code.  You don't notice it on modern desktops, but it really does hurt on older machines.  I don't really buy the argument that 6.8.2 causes slowdowns (I certainly haven't seen any myself, and there really is almost no difference between 6.8.1-1ubuntu16 and 6.8.2-1; I dare say that most of the people feeling a difference after downgrading were just feeling it because their CPUs were scaled up to full speed after having installed a bunch of packages and started up X for the first time, so I would say that most of the '6.8.1 is faster stuff' is really just #1 again).

Three: Badly configured nVidia drivers, or maybe even broken nVidia drivers.  I can't help here -- because it's binary, I can't debug it and work out where it's going wrong, if at all.  Or it might just be a configuration issue, since nvidia and fglrx are both very fiddly compared to standard open source drivers.  You could ask nVidia, but they'd more likely than not tell you were on your own and claim it's some form of Ubuntu-specific issue, or configuration issue.

---

### Post by JGJones on 2005-03-10
Fair enough I understand what you're saying. It's just that switching windows etc is painfully slow due to the xorg taking up CPU resources - I would have expected this to be done in hardware by the graphics card instead of the CPU doing the work - my laptop which is just a P2 400MHz with 64Mb currently runs Windows 2000 and it have the feel that it's much faster due to windows and the like being redrawn at once despite the fact that my Ubuntu system is a much faster machine having P3 800MHz and 256Mb with 3D card.

I think you are right in that it's the video drivers that's an issue having gotten it from Ubuntu synaptic package manager, but not coded by you. I guess I'll try installing the nvidia installer from the nvidia website but I have doubts that'll work.

One question - xorg/xfree - it is supposed to be drawn by the card and not suck up CPU power right? At least not to the extent that we're experiencing.

---

### Post by rblee on 2005-03-11
Okay, I just upgraded my hoary install from Xorg 6.8.1.902 to 6.8.2. I *also* upgraded my kernel at the same time. (Well, and a truckload of other packages, but those are the two that should directly affect this.)

I've got a radeon 8500 QL (AGP), I'm not running powernowd, I've got an Athlon 1700 system. (A bit creaky, but not horrible.)

After the upgrade and restarting the server, top is showing Xorg taking 84-90% CPU time for 15+ second intervals, after I either switch windows (for example, between two xterms where one was obscuring the other), or between two tabs in epiphany. It makes the system nearly unusable. (Watches it for a bit more.) Heck, sometimes it pops back up to big CPU usage all on it's own (not touching the mouse or keyboard), but that could be due to the constant rendering of of processes running right now on other workspaces.

I'm going to reboot back into kernel 2.6.10 (in .11 right now) and see if that makes any difference.

---

### Post by JGJones on 2005-03-16
Some big updates today - which was new kernal, new xorg version, new nvidia-glx driver version (still 6629 but a update nonetheless from ubutnu) and many other stuff...

Xorg is still taking up large CPU resources.

It's still to see Firefox taking up 20% CPU (when downloading a webpage) which I can accept but seeing xorg taking up 60% or higher CPU resources to display the page as it's being downloaded - this lead to the system feeling extremely slow. In comparasion, if I do the same in Windows on the same machine, Firefox take about the same CPU resources but the rest of CPU are at idle - graphics are extremely snappy and show at once - which is how it should be in Linux. 

I wanna kill off Windows from this machine but am unable to do so until xorg stop sucking up so much CPU resources. I know using alternative windows manager apart from Gnome helps but that's not my aim - I like Gnome on Ubuntu - it's clean and simple so I'll like to stick to default.

My system's a slower one than the one above, but on Windows it's smooth and responsive while on Linux it feel like I have an 386 PC due to Xorg robbing CPU cycles.

---

### Post by JGJones on 2005-03-16
For those that are not following the bug on Ubuntu bugzilla - a guy posted this:

> I have exactly the same problem. I am running a dual-opteron with 8Gb and a
Nvidia GForce 5900.

So it's not just affecting slow PC's but screaming fast machines as well.

---

### Post by p!=f on 2005-03-18
After the latest updates my problem is back.
[quote=daniels]
You don't notice it on modern desktops, but it really does hurt on older machines.
[/quote]
Perhaps you noticed some posts here which showed some of us DO NOT have old or older hardware.
Perhaps you just don't want to understand that the same hardware shows completely different performance under GNOME and under KDE. GNOME is crawling, KDE is running like a charm.
Even I posted my problem three times here I did not get any technical answer or point me how to solve the issue so I write it for the fourth time:
As soon as I start the machine and login, open gnome-terminal, give the system some time to finish loading and type "top", Xorg process eats 13% of the CPU power (the system is idle, hands off of a keyboard and a mouse) all the time (5 mins, 10, 15, pick your number). Relogin solves this by decreasing consumption to 2,7% and making GNOME running really smoothly.
So I created new user account, did not change a single thing in the profile and? Yes, 9%. After relogin, here we go, 2,7%.
So I reinstalled the machine (from Warty minimal custom, no X installed), dist-upgraded and here we go, problem is back.
Looks like it's not xorg.conf related but as I said it's GNOME/GTK+ related. Changing nvidia driver to nv makes no difference on CPU consumption. Powernowd purged. Any ideas anyone?

---

### Post by zep24 on 2005-03-18
Do you have the line

```
Option "BackingStore" "true"
``` 

in the Device section of your xorg.conf? If you don't, add it and see if it helps.

---

### Post by JGJones on 2005-03-18
Option "BackingStore" "true"

Yes just done that and no difference.

As mentioned - running top in a maximised terminal window (that is, it's taking up the whole desktop space) and my resolution is 1600x1200.

Top shows xorg taking about 12% JUST to show the terminal windows updates for top. There is no other programs running and it is a freshly booted system. Restarting xorg make no difference either.

I guess what p!=f said earlier seems it's a Gnome issue. I've got no desire to install KDE on my Ubuntu system, I would like to keep it default, as I am testing Ubuntu for use for newbies and if they see a slow GUI, they'll think Linux is rubbish which it's not but newbies being newbies...

Apart from that issue - which is a pain, Ubuntu does everything else wonderfully which is why I intend to stick with it instead of jumping ship.

The bug is at P1 priority so the devs are aware of it, let's hope they resolve it soon but they do have a lot of work to do, with Hoary release date coming closer.

---

### Post by JGJones on 2005-03-21
[QUOTE=JGJones]Option "BackingStore" "true"

Yes just done that and no difference.

As mentioned - running top in a maximised terminal window (that is, it's taking up the whole desktop space) and my resolution is 1600x1200.

Top shows xorg taking about 12% JUST to show the terminal windows updates for top. There is no other programs running and it is a freshly booted system. Restarting xorg make no difference either.

I guess what p!=f said earlier seems it's a Gnome issue. I've got no desire to install KDE on my Ubuntu system, I would like to keep it default, as I am testing Ubuntu for use for newbies and if they see a slow GUI, they'll think Linux is rubbish which it's not but newbies being newbies...

Apart from that issue - which is a pain, Ubuntu does everything else wonderfully which is why I intend to stick with it instead of jumping ship.

The bug is at P1 priority so the devs are aware of it, let's hope they resolve it soon but they do have a lot of work to do, with Hoary release date coming closer.[/QUOTE]
 I decided today to install Kubuntu as I would like to help the devs where I can with the bug of terrible 2D performance in Gnome.

In kdm (KDE Desktop Manager) I then ran Kterminal (KDE's own terminal) and maximised it and run top.

xorg is taking at MOST 0.1% of CPU.

I closed the terminal and ran Gterminal (Gnome's terminal) and maximised it and ran top.

xorg is taking up to 18% CPU resources when top updates (basically a screen refresh of the terminal) which is terrible really.

This incidates that Gnome have a problem with nvidia drivers as so far no-one with ATI is having the same problem.

Finally to forum moderators - this should be moved into Hoary xorg forum as it's all about Hoary and xorg.

Many thanks

---

### Post by daniels on 2005-03-21
You're right in that it's a problem with the nVidia drivers.

The difference between KDE and GNOME (read: between Qt and GTK) in this regard, is that the latter makes very extensive use of the Render extension, and the former does not.  The reason why GTK apps appear slow and Qt apps appear fast is that Render is for some reason slow in the nVidia drivers.

And I can't even begin to tell you why, because they're binary drivers, so I have no idea what's going on.  Sorry.

---

### Post by duff on 2005-03-21
I've had my laptop with Ubuntu getting *really* slow the last couple of weeks.  It's a P4 2GHz, with a radeon 7500.  It think I've got the craziest Xorg process out there...it'll just start running at 90% and heats the computer so much I have to turn it off (the keyboard literally hurts to touch).  I've tried dropping down to Xfce to see if that would lighten the load, but in the week or so I've been using it, it's still bad.  And it's been doing this with the 2.6.10 kernels (releases 2,3&4), and I can't try the 2.6.11 since that hardlocks the computer while booting X.

I just found this thread, and I'm at work, so I'll try some of the suggestions already posted when I get home.  I just wanted to chime in with my problem while it was on my mind.

---

### Post by recmar on 2005-03-21
Hello!
Somehow I can't agree with you guys that the problem is graphic driver for nVidia. My comp is Acer laptop with build in VIA/S3 KN/KM400 graphics, AMD Athlon 2400 and 768 SDDRAM and have exactly same problem with 2D. Still can't wait for some solution. I'm just sick of well known OS and would like to move to Ubuntu for good.

---

### Post by gnutux on 2005-03-21
It seems this problem only happens with GNOME, it's working fine here with KDE. I have no redraw problems when moving the windows. Also, X.Org doesn't take upto 90% of system CPU, most is only 2-5%

System SPECS:
Samsung NV 5000 Laptop
Intel Pentium III 701 MHZ Coppermine
20 GB HDD
192 MB RAM
KUBUNTU 5.04 Preview
S3 Savage  16 MB Video Card

and on my desktop, it's working fine with NVIDIA drivers and KDE. I have SUSE Linux 9.2 installed and XORG doesn't take alot of CPU. It's only taking uo 2% of CPU.

System SPECS:
Custom built
Intel Pentium IV 2533 MHZ (2.53 GHZ)
200 GB HDD
512 MB RAM
SUSE Linux 9.2 and Windows XP Pro
NVIDIA GeForce 4 Ti 4200 w/ AGP 8x 128MB GFX card

gnutux

---

### Post by fackamato on 2005-03-21
I can confirm that it's a gnome problem. Damn :(. Works fine with fluxbox for example.

---

### Post by jayavarman on 2005-03-22
Don't really know about the most of you but for me the problem was powernowd. At least in version 0.90-3ubuntu12.

If your computers are crawling just do something like "cat /proc/cpuinfo" and check those MHz. If they are too low do "sudo /etc/init.d/powernowd stop" and enjoy  8) 

Rui

---

### Post by Leszek Tarkowski on 2005-03-22
I got two hoary systems running - my notebook (Pentium M 1.6 + Radeon 9600 + 512 MB RAM) + desktop at work (Barton 2500+ + Radeon 9200 + 1GB RAM). I also see that X are eating cpu especially when resizing windows. eg. resizing terminal (gnome-terminal or xterm) running top causes X to utilize 60% of cpu (on my desktop - on laptop is similar (even higher) but i don't have it right now).
On desktop I have radeon driver, on notebook fglrx. So it is independent (ati,nvidia) or binary/open drivers.
I didn't testet it under kde. Maybe today later - i'm really busy.
On desktop i don't have cpu clock daemon. On notebook of course yes.

---

### Post by mr_ed on 2005-03-22
My laptop, with powernowd disabled, running top in a window on my PIII 1GHz 256MB RAM
Xorg
idle 5-7%
resizing the window ~70%
moving a window ~60% -- others processes bring it up to 100%

My work machine, PIV 3.0GHz 512MB RAM running Windows XP
system
idle 4-5%
resizing a window ~ 56-60%
moving a window - anywhere from 30-60%

All of that seems ok to me when put into perspective...

My problem (which should be in another thread) is that everything is slow!  (if anyone can point me to the right thread I'd appreciate it)
11 seconds to open gedit
12 seconds to open firefox
2 seconds to open calculator (usually this is more, but I bet libraries have already been loaded)

11 seconds to open a text editor?!  What is up with that?
I know it's a bad comparison, but it's 12 seconds to load Firefox on my laptop to less than 1 second on my work machine running Windows.

---

### Post by JGJones on 2005-03-22
[QUOTE=daniels]You're right in that it's a problem with the nVidia drivers.

The difference between KDE and GNOME (read: between Qt and GTK) in this regard, is that the latter makes very extensive use of the Render extension, and the former does not.  The reason why GTK apps appear slow and Qt apps appear fast is that Render is for some reason slow in the nVidia drivers.

And I can't even begin to tell you why, because they're binary drivers, so I have no idea what's going on.  Sorry.[/QUOTE]

Just ensuring this get to end of thread for new readers :)

I'm leaving it until new drivers come out.

However interestingly enough I installed xcompmgr with transest - whilst xorg still used up CPU, the system felt faster in some minor way. I don't know how to describe, but it does suggest the drivers like you've mentioned.

However thanks for your help. Here's to waiting for updated drivers from NVidia :)

EDIT - Nvidia have released new drivers - 
Version: 1.0-7167
Operating System: Linux IA32
Release Date: March 11, 2005

There are guides for installing it yourself in the forums, but I would recommend you wait until it's added to the resposity (make for easier installation and uninstallation)

However for those who are going to install it anyway, please post results of how it fares with Render :)

---

### Post by Dracontopes on 2005-03-23
I can confirm that it's NOT a Nvidia problem! I'm running Ubuntu Hoary on an Ati Radeon 9700pro, direct rendering is enabled.

 ```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Pro Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

``` 

And yes, resizing/moving ANYTHING with windows just pumps up CPU usage to 70/80%

(AMD Athlon XP-M 2400 Mhz (~3500+), Asus a7n8x del. (nforce2))

---

### Post by fackamato on 2005-03-23
[QUOTE=Dracontopes]I can confirm that it's NOT a Nvidia problem! I'm running Ubuntu Hoary on an Ati Radeon 9700pro, direct rendering is enabled.

 ```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Pro Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

``` 

And yes, resizing/moving ANYTHING with windows just pumps up CPU usage to 70/80%

(AMD Athlon XP-M 2400 Mhz (~3500+), Asus a7n8x del. (nforce2))[/QUOTE]

I guess it's a gnome problem then.

---

### Post by wmcbrine on 2005-03-23
[QUOTE=mr_ed]My problem (which should be in another thread) is that everything is slow!  (if anyone can point me to the right thread I'd appreciate it)
11 seconds to open gedit
12 seconds to open firefox
2 seconds to open calculator (usually this is more, but I bet libraries have already been loaded)[/QUOTE]
Check the results of "hdparm /dev/hda" (or whatever your main drive is). On my system, multcount was not enabled by default (which didn't seem to make a difference overall, but totally killed my high-def video playback). My DVD burner didn't have DMA enabled (a more serious problem, especially if it's not enabled on your hard drive).

Oh, yeah, and get more RAM.

---

### Post by p!=f on 2005-03-23
I noticed when I restart GDM on the first boot I did not experience that annoying bug (Xorg taking 13% CPU power after the first login) so I tried to compile my own GDM from sources. It did not help. However, my problem  was solved by GDM upgrade yesterday.
```

[~] > dpkg -l gdm
ii  gdm                            2.6.0.7-0ubuntu3               GNOME Display Manager

```
Note: The offending version was 2.6.0.7-0ubuntu1

Thank you!

---

### Post by JGJones on 2005-03-23
After doing a bit of reading it appears that Gnome is doing new stuff, making large uses of Render extensions, but lot of it is still experimental hence it might not always work with video cards such as nvidia. Likewise for xorg which did split from xfree86 and is also doing new stuff.

However I like their aim, to bring eye candy which I believe Gnome have the better "eye candy" over KDE and is cleaner to use. I guess it's a time of waiting until the code get tweaked a bit more so that it's more reliable and make better use of video card and likewise for Nvidia's new drivers.

Now all Gnome need is a decent menu editor and I'm happy despite the CPU hit which is still extremely annoying so Windows XP is still my main system, but once it's better optimised I'll switch. It's the only factor stopping me.

---

### Post by Firetech on 2005-03-25
I've tried to solve the problem using the kubuntu-desktop package, but for me, the cpu flies when I move windows, both in KDE and Gnome... It might be GTK or X.org, or both. Anyone with XFree86 experiencing this problem?
It seems to affect more Hoary users than Warty users, too.
I just hope they solve the problem soon, although I can live with it... (I have more than sufficient cooling on my CPU...)

---

### Post by negatory on 2005-03-26
I'm not having this problem at all in Hoary. I'm using an Athlon 3500+, 1GBram  with Hoary 64 bits and when I'm using my gnome desktop with System monitor applet,firefox,amule,evolution and xmms (to name a few...) my XOrg takes from 1.7% cpu to 6.7%,when resizing a window it takes 30% at most.I'm using a nvidia 6600 PCIE with 256 ram,could that do the trick?
And I'm not using "RenderAccel" should I enable it?What does it do exactly?
Thanks!
Pedro Carrico

---

### Post by Dracontopes on 2005-03-27
I've enabled reduced_resources in Gnome, so when moving windows the contents of the window are not displayed. CPU usage is lower now, but this is only a temproary solution I hope...

---

### Post by Firetech on 2005-03-27
[QUOTE=negatory]And I'm not using "RenderAccel" should I enable it?What does it do exactly?[/QUOTE]
Only use RenderAccel if you have the nvidia drivers installed, what it does is  (as far as i get it from nvidia's readme) to use the hardware acceleration for the Render extension (which Gnome/GTK apparently use a lot). What the Render extension is for is out of my knowledge, though... I guess it is used to render the screen...

[QUOTE=Dracontopes]I've enabled reduced_resources in Gnome, so when moving windows the contents of the window are not displayed. CPU usage is lower now, but this is only a temproary solution I hope...[/QUOTE]
Where do you do that?

---

### Post by Dracontopes on 2005-03-27
In GConf editor:
Go to "apps -> metacity -> general"

The key is called "enable reduced_resources"

Or you can just search for it in Gconf.

---

### Post by Firetech on 2005-03-27
[QUOTE=Dracontopes]In GConf editor:
Go to "apps -> metacity -> general"

The key is called "enable reduced_resources"

Or you can just search for it in Gconf.[/QUOTE]
Thanks, that helped a bit (as for you)...
It can make the waiting for a fix more bearable... But it is still some kind of solution.

I just cant understand why there are more Hoary users experiencing this, while some  (less than Hoary) Warty users have it anyway...

---

### Post by Dracontopes on 2005-03-29
There seems to be an update for xorg almost everyday now, hopeful...

---

### Post by kiddo on 2005-03-30
There is a lot of updates these days, hopefully we may be able to use render accel soon... Anyways, I wanted to ask if sucessful users could do some kind of guide (maybe in the wiki? I haven't seen any yet)... or maybe we'll just have to wait.. I haven't tried the render acceleration for a month, it was making xorg crash... However, I removed the 1.0-7xxx driver from nvidia (which was unusable for me, no GL at all) and put back the nvidia-glx package... Maybe I should give it a try again since there has been so many xorg updates this week...

---

### Post by Firetech on 2005-03-30
[QUOTE=kiddo]There is a lot of updates these days, hopefully we may be able to use render accel soon... Anyways, I wanted to ask if sucessful users could do some kind of guide (maybe in the wiki? I haven't seen any yet)... or maybe we'll just have to wait.. I haven't tried the render acceleration for a month, it was making xorg crash... However, I removed the 1.0-7xxx driver from nvidia (which was unusable for me, no GL at all) and put back the nvidia-glx package... Maybe I should give it a try again since there has been so many xorg updates this week...[/QUOTE]
 I had a lot of problems with the 1.0-7xxx driver from nVidia (segmentation faults everywhere), so I've installed the 1.0-6xxx driver from nVidia with the patches from nvnews.com (official patches) and it's running like clockwork, except the CPU problem that this thread is about... 3D is working fine, but the nvidia driver isn't accelerating 2D...

In short terms: the 1.0-7xxx driver from nvidia is buggy, the 1.0-6xxx driver is better, but for me, the 2D problem is still there.

---

### Post by jonny on 2005-03-30
To try to get to understand this better, I've been doing some testing on different gnome distributions (all live CDs except Hoary).  Using the highly unscientific methods of averaging 10 instances of:
 - the Xorg/XFree86 CPU usage reported by the top command
 - the glxgears frame rate when running in an unmaximised window
here are the results:

[B]System 1: Athlon 650, nVidia GeForce 256
[/B]Hoary (Gnome 2.10; nvidia 1.0.6629; Xorg): 11.2%; 1088 fps
Hoary (Gnome 2.10; nv; Xorg): 3.8%; glxgears unavailable
Warty (Gnome 2.8; nv; XFree86): 2.7%; glxgears unavailable
Beatrix (Gnome 2.8; nv; XFree86): 4.7% of cpu; glxgears unavailable
Sun Java Desktop (Gnome 2.2; nvidia 1.0-4496; XFree86): 2.0%; glxgears 176 fps
Sun Java Desktop (Gnome 2.2; nv; XFree86): 1.9% glxgears unavailable
I also tested on Mepis (KDE based).  I've lost the exact result, but it was approximately 0.1% CPU.

**System 2: P4 2.8GHz Intel 82852 / 855GM integrated graphics**
Hoary (Gnome 2.10; i810 driver; Xorg): 1.1%; glxgears 550 fps

Some observations
1. The problem seems to be hardware dependent.  Earlier posters have reported problems with both nVidia and ATI chipsets, but my Intel integrated graphics run fine.
2. Only 2D performance is affected
3. Only recent versions of Gnome are affected.  KDE is completely unaffected (as is Windows!)
4. The problem existed in Warty but became much more severe in Hoary
5. Both the nv and nvidia drivers are slow, but nvidia is much worse
6. Draw comfort from the good 3D performance of the 6629 nvidia drivers.  It's improved six-fold since the 4496 release.
7. This is not drawn from the above results, but some other recent Gnome distros are unaffected.  A colleague switched from Hoary to Fedora to tackle his performance issues, and, although he didn't take measurements, his system perceptibly speeded up.  Fedora don't make a live CD, so I couldn't include it in my tests.

I doubt if this will help anyone find a solution, but it might help to firm up the anecdotal evidence reported by others. We have a problem, and if it's not fixed it will drive people away from ubuntu.

I note that nVidia have released a patch (not yet in the Hoary repositories) that is aimed at 'restoring the 2D performance of 6-series drivers to that of earlier releases'.  Has anyone tried it?

---

### Post by Leszek Tarkowski on 2005-03-31
[QUOTE=jonny]To try to get to understand this better, I've been doing some testing on different gnome distributions (all live CDs except Hoary).  Using the highly unscientific methods of averaging 10 instances of:
 - the Xorg/XFree86 CPU usage reported by the top command
 - the glxgears frame rate when running in an unmaximised window
here are the results:

[B]System 1: Athlon 650, nVidia GeForce 256
[/B]Hoary (Gnome 2.10; nvidia 1.0.6629; Xorg): 11.2%; 1088 fps
Hoary (Gnome 2.10; nv; Xorg): 3.8%; glxgears unavailable
Warty (Gnome 2.8; nv; XFree86): 2.7%; glxgears unavailable
Beatrix (Gnome 2.8; nv; XFree86): 4.7% of cpu; glxgears unavailable
Sun Java Desktop (Gnome 2.2; nvidia 1.0-4496; XFree86): 2.0%; glxgears 176 fps
Sun Java Desktop (Gnome 2.2; nv; XFree86): 1.9% glxgears unavailable
I also tested on Mepis (KDE based).  I've lost the exact result, but it was approximately 0.1% CPU.

**System 2: P4 2.8GHz Intel 82852 / 855GM integrated graphics**
Hoary (Gnome 2.10; i810 driver; Xorg): 1.1%; glxgears 550 fps

Some observations
1. The problem only seems to occur with nVidia GPUs
2. Only 2D performance is affected
3. Only recent versions of Gnome are affected.  KDE is completely unaffected (as is Windows!)
4. The problem existed in Warty but became much more severe in Hoary
5. Both the nv and nvidia drivers are slow, but nvidia is much worse
6. Draw comfort from the good 3D performance of the 6629 nvidia drivers.  It's improved six-fold since the 4496 release.
7. This is not drawn from the above results, but some other recent Gnome distros are unaffected.  A colleague switched from Hoary to Fedora to tackle his performance issues, and, although he didn't take measurements, his system perceptibly speeded up.  Fedora don't make a live CD, so I couldn't include it in my tests.

I doubt if this will help anyone find a solution, but it might help to firm up the anecdotal evidence reported by others. We have a problem, and if it's not fixed it will drive people away from ubuntu.

I note that nVidia have released a patch (not yet in the Hoary repositories) that is aimed at 'restoring the 2D performance of 6-series drivers to that of earlier releases'.  Has anyone tried it?[/QUOTE]
 Also radeon systems are affected. Both my notebook and desktop (9600 and 9200 respectively). both fglrx and radeon drivers. See my previous post. I think about dropping gnome and giving kde a chance...

---

### Post by JGJones on 2005-03-31
[QUOTE=jonny]I doubt if this will help anyone find a solution, but it might help to firm up the anecdotal evidence reported by others. We have a problem, and if it's not fixed it will drive people away from ubuntu.

I note that nVidia have released a patch (not yet in the Hoary repositories) that is aimed at 'restoring the 2D performance of 6-series drivers to that of earlier releases'.  Has anyone tried it?[/QUOTE]

Quite a few people here are using cards older than the 6-series drivers (for example I use GeForce FX5200)

I've submitted it as a bug but it seem to have ended up being a powernowd bug instead of anything to do with graphics.

Driving people away from Ubuntu - I agree completely, while showing people Ubuntu, the comments I get are that it look clean but it's slow isn't it?

As for me...I've switched to using KDE...not what I want since I like the clean layout of Gnome but I got fed up with the slow speed.

However we have to bear in mind that it's possible the developers can't do very much - Gnome is working toward 2.10 and doing big things with it, likewise for the GTX+ but I still think it can be quicker than it is now!!

I'll like to hear developer's thoughts on this since obviously they know what's happening inthe Linux world more than I would! :)

---

### Post by jonny on 2005-03-31
> Quite a few people here are using cards older than the 6-series drivers (for example I use GeForce FX5200)I meant older versions of the nvidia driver, such as that used by the Sun Java Desktop, not older graphics card.  The same driver works with pretty much all nVidia cards made in the last few years.  However, Leszek's post suggests that the nvidia driver might not be to blame after all.

---

### Post by jonny on 2005-03-31
**Leszek Tarkowski,** I've corrected my conclusions to take account of your problems with an ATI card.  I really don't know how I managed to miss your earlier posting - I mistakenly thought all the ATI users had gone away happy with the powernowd, dma, etc tips.

---

### Post by Slapdash on 2005-03-31
I recon then I should wait before I install hoary since my Warty is doing fine with Default install?

---

### Post by Firetech on 2005-03-31
Hmm. Might it help by using Xfree86 instead of x.org?

[QUOTE=jonny][B]System 1: Athlon 650, nVidia GeForce 256
[/B]Hoary (Gnome 2.10; nvidia 1.0.6629; Xorg): 11.2%; 1088 fps
Hoary (Gnome 2.10; nv; Xorg): 3.8%; glxgears unavailable
Warty (Gnome 2.8; nv; XFree86): 2.7%; glxgears unavailable
Beatrix (Gnome 2.8; nv; XFree86): 4.7% of cpu; glxgears unavailable
Sun Java Desktop (Gnome 2.2; nvidia 1.0-4496; XFree86): 2.0%; glxgears 176 fps
Sun Java Desktop (Gnome 2.2; nv; XFree86): 1.9% glxgears unavailable
I also tested on Mepis (KDE based).  I've lost the exact result, but it was approximately 0.1% CPU.[/QUOTE]

Why didn't you try the nvidia driver of the Warty Live CD? (For me that's not working, screen says something like "Sync out of range")
You could also try the GamesKnoppix CD which is based on Knoppix but with 3D support and games instead of important software. The original Knoppix CD also has support for installing the nvidia driver...

---

### Post by jonny on 2005-03-31
> Why didn't you try the nvidia driver of the Warty Live CD? (For me that's not working, screen says something like "Sync out of range")
You could also try the GamesKnoppix CD which is based on Knoppix but with 3D support and games instead of important software. The original Knoppix CD also has support for installing the nvidia driver...I didn't realise that the Warty live CD had the nvidia driver available.  I'll try later to see what the results are.

I didn't try Knoppix, as my results with Mepis (and others' experience here) showed that this is definitely a Gnome problem.  I take the point about the 3d drivers, though - Mepis defaults to nv, not nvidia, on my system.

How would I set about using XFree86 on Hoary without destroying my system?

---

### Post by jonny on 2005-03-31
[QUOTE=Slapdash]I recon then I should wait before I install hoary since my Warty is doing fine with Default install?[/QUOTE]You might want to wait if you have a slow system, or if you like to run high screen resolutions.  I used 1280x1024 for testing, but 1600x1200 has nearly 50% more pixels to draw.  That's a lot of extra CPU cycles when simply redrawing a terminal window every 5 seconds takes up more than 10% of your PC's brain power.

The colleague who dumped ubuntu in disgust was running a brand new development box (fast pentium 4, 1GB RAM but only integrated graphics) at very high screen resolutions.  He found that even web browsing was unbearable with a fully maximised window - after touching the mouse wheel he could almost go away and make a cup of tea while the processor caught up.

But then again, you might strike lucky.  Hoary's great on my laptop.

---

### Post by Firetech on 2005-03-31
[QUOTE=jonny]I didn't realise that the Warty live CD had the nvidia driver available.  I'll try later to see what the results are.[/QUOTE]
It is available via some kind of advanced menu, can't really recall the exact menu, mut it is explained on the startup screen, just make sure it doesn't autostart directly.

[QUOTE=jonny]I didn't try Knoppix, as my results with Mepis (and others' experience here) showed that this is definitely a Gnome problem.  I take the point about the 3d drivers, though - Mepis defaults to nv, not nvidia, on my system.[/QUOTE]
I don't really know about that... I tried installing kubntu-desktop on my machine, and the problem only partially disappeared... Moving windows and scrolling in Firefox still sucked CPU, although top in Konsole (maximized) showed xorg using like 0.3% CPU (while a maximized gnome-terminal window used about 10%, also in KDE). I think it's a GTK+ or X.org problem, or the combination...

[QUOTE=jonny]How would I set about using XFree86 on Hoary without destroying my system?[/QUOTE]
Tricky one... I'm not entirely sure, but I think (from real Debian experiences) that you just have to "apt-get install xserver-xfree86" (as root/sudo), and then the configuration should ask you which one of xserver-xorg and xserver-xfree86 you want to use.
To reset it (probably in console...) run dpkg-reconfigure xserver-xorg (as root/sudo, and NO space between dpkg and -reconfigure).
You probably would want someone to confirm this before trying, as I'm no expert on Linux... (Read a bit in [this thread](http://ubuntuforums.org/showthread.php?t=3790), although it is the other way around...)
I think that you safely can install the xserver-xfree86, though.

---

### Post by JGJones on 2005-03-31
It was the same issue with xfree86 if I recall but worth testing if anyone have a spare machine to try it out.

It's definetely to do with GTX+ which Gnome make use of. The developer that posted in here earlier explained that KDE use QT while Gnome use GTX+ - which is why KDE appears to be faster redrawing displays etc over Gnome with GTX+

Gnome is now at version 2.10, so it's probably to do with GTX+ but I wouldn't have a clue about that.

However the latest nvidia driver (7129) is now available thru Ubuntu reposity update and I've installed that along with the latest available Gnome files and xorg files....

Any difference? At first I thought there was as it appeared to be faster....yippee! Until I realised I had reduced_resources enabeld for metacity. So I unticked that  and with top running in a terminal window to side, I then resized a window which is showing just text....just text and nothing fancy, no graphics.

xorg shot up to 80% CPU usage and the resizing of the windows was hideous, extremely jerky and very slow and the system slowed down to a crawl. My desktop resolution is 1600x1200 so it eats more CPU cycles for me.

Come on developers...there's people in here with problems, and we'll like to know how to bloody solve it. I'm getting too close to ditching Ubuntu sometime (I don't want to as I do really like this product)

Latest nvidia drivers...latest Gnome version....latest xorg version....and STILL high CPU usage that slows a system down to a crawl JUST to resize a window (which is frankly stupid really....I had a laptop running P2 400MHz with just 64Mb and I slapped winXP on it for testing and it resized windows very quickly and SMOOTHLY and WinXP is a resource hog for that system!!!)

here is my xorg.conf file if it helps....
```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
#	Load	"GLXCore"
#	Load	"dri"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbVariant"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Extensions"
	Option 		"Composite" 	"Enable"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection

Section "Monitor"
	Identifier	"HM903DB/DTB"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"HM903DB/DTB"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
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

```

As you can see I do have RenderAccel enabled...

Also the new nvidia drivers are worth getting....the 3D speed boost is huge....previously I was gettin about 600 fps in glxgears, now I am getting over 900fps...impressive.....but please someone help us with the hideous 2D performance....it sucks....it's spoiling what is otherwise a fantastic distro!

---

### Post by kiddo on 2005-03-31
Hey people, I realized the 7167 line of nvidia-glx driver packages just appeared in the Hoary repository! I am, however, reluctant to installing it. Anyone here did test the new package? If I want to test it, what would be the apt-get command to revert to the previous 6629 package? In fact... there should be no way to go back except installing the official nvidia driver right? That's the first time I'm a little hesitant of doing an apt-get upgrade :)

Edit: if I understood correctly, JGJones must have used the 7xxx drivers...

---

### Post by jayavarman on 2005-03-31
Maybe this [1] info is relevant here.

[1] [http://ubuntuforums.org/showthread.php?t=23130](http://ubuntuforums.org/showthread.php?t=23130)

---

### Post by jonny on 2005-03-31
> Hey people, I realized the 7167 line of nvidia-glx driver packages just appeared in the Hoary repositoryWell, I just went for it.  And what a difference: when running top, Xorg now consumes 7.6% of CPU, down from 11.2% with the old drivers.  That's still not good enough, but it's a lot better.  3D performance is unaffected but, interestingly, both 2D and 3D performance are slowed by about 10% when using the often cited RenderAccel true and nvAGP 1 options in xorg.conf.

More important than raw CPU cycles is user perception, though.  I no longer get a horrible ripple-down effect whenever the screen is redrawn, and scrolling is *much* more responsive.  Hard to measure, perhaps, but immediately noticeable.

For me, it's good enough.  Thanks to the packagers for getting this fix out so soon after its release by nVidia a few days ago.  And sorry to the ATI guys, for whom help is not yet at hand.

On a related not, I notice that nVidia have released a new driver today (not yet in the repositories) that purports to address some performance issues - there's a link to it in another thread in this forum that I've since lost.  Anyone brave enough to try it?

---

### Post by JGJones on 2005-04-01
[QUOTE=kiddo]Hey people, I realized the 7167 line of nvidia-glx driver packages just appeared in the Hoary repository! I am, however, reluctant to installing it. Anyone here did test the new package? If I want to test it, what would be the apt-get command to revert to the previous 6629 package? In fact... there should be no way to go back except installing the official nvidia driver right? That's the first time I'm a little hesitant of doing an apt-get upgrade :)

Edit: if I understood correctly, JGJones must have used the 7xxx drivers...[/QUOTE]


Yes I used the 7167 version (sorry used the wrong number in my post)....it's worth it for the 3D boost which is quite large, but no difference to 2D

---

### Post by JGJones on 2005-04-01
[QUOTE=jonny]Well, I just went for it.  And what a difference: when running top, Xorg now consumes 7.6% of CPU, down from 11.2% with the old drivers.  That's still not good enough, but it's a lot better.  3D performance is unaffected but, interestingly, both 2D and 3D performance are slowed by about 10% when using the often cited RenderAccel true and nvAGP 1 options in xorg.conf.

More important than raw CPU cycles is user perception, though.  I no longer get a horrible ripple-down effect whenever the screen is redrawn, and scrolling is *much* more responsive.  Hard to measure, perhaps, but immediately noticeable.

For me, it's good enough.  Thanks to the packagers for getting this fix out so soon after its release by nVidia a few days ago.  And sorry to the ATI guys, for whom help is not yet at hand.

On a related not, I notice that nVidia have released a new driver today (not yet in the repositories) that purports to address some performance issues - there's a link to it in another thread in this forum that I've since lost.  Anyone brave enough to try it?[/QUOTE]

The scrolling down of Firefox is much smoother that's true. But resizing windows etc, you'll get horrible ripple down effect (providing you're not using reduced resources of metacity in gconf) which take up to 70-80% on my CPU

---

### Post by JGJones on 2005-04-01
Slow Firefox...

There is an alternative, which is refreshing quick and is excellent...

BUT it is adware (you get a small banner at top showing results from Google) or you can buy it.

Download Opera in debian unstable package and to install:

sudo dpkg -i opera-<version number>.deb

It won't add entries to menu so to run type opera or add a launcher to the panel at top (until we get a menu editor that is)

There is no slow down that I get with Firefox....but then Opera seems to be based on a older version of GTX+ - it look good but it's not following standard Gnome look hence the thoughts it's based on old GTX+...but it make it very quick to use so I don't mind the ads at top (I use Opera in Windows, so I'm happy to purchase it for Linux)

---

### Post by MiddleBrooker on 2005-04-01
HI,
sorry but in this thread seems that the probles is only on Nvidia graphics cards, but actually I've an AMD 64bit with Nforce3 Mainboard and a RADEON 9800PRO by Hercules, so the resizing of a gnome terminal on my desktop take the 100% of CPU!

Here is my /etc/X11/xorg.conf , please can somebody tell me where is my problem?

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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "Extensions"

Option "Composite" "Enable"

EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option "backingstore" "true" 

# If X refuses to use the screen resolution you asked for,
# uncomment this; see "Bugs and Workarounds" for details.
	 Option 	"NoDDC"
# === Video Overlay for the Xv extension ===
  	Option 		"VideoOverlay" "on"
        Option          "CursorShadow" "1"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
  	Option 		"OpenGLOverlay" "off"

# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
  	Option 		"UseInternalAGPGART" "no"
EndSection

Section "Monitor"
	Identifier	"Flatron 915FT Plus "
	Option		"DPMS"
	HorizSync	30-107
	VertRefresh	50-200
#	DisplaySize	270	203	# 1024x768 96dpi
#	DisplaySize	338	254	# 1280x960 96dpi
#	DisplaySize	338	270	# 1280x1024 96dpi
#	DisplaySize	370	277	# 1400x1050 96dpi
#	DisplaySize	423	370	# 1600x1400 96dpi
#	DisplaySize     423     317.5   # 1600x1400 96dpi
         DisplaySize     508     381     # 1920x1440 96dpi
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"Flatron 915FT Plus "
	DefaultDepth	24

	SubSection "Display"
		Depth		24
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

```

I've also tried to leave out all the custom options under the "Device" Section and use only:

Option 		"UseInternalAGPGART"    "no"	
Option           "backingstore"               "true" 

but nothing is change!!!

Thanks for all the HELP!!! ...... and HELP PLEASE!!!
This problem is driving me MAD!!!

Best Regards,

MiddleBrooker

---

### Post by Firetech on 2005-04-01
[QUOTE=jonny]On a related not, I notice that nVidia have released a new driver today (not yet in the repositories) that purports to address some performance issues - there's a link to it in another thread in this forum that I've since lost.  Anyone brave enough to try it?[/QUOTE]
[http://www.nvidia.com/object/linux_display_ia32_1.0-7174.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7174.html)
I'll get to trying it now, as I can't run the repository drivers because I'm using a custom kernel.
Although, I just think it's a released version of the 7167 with the patches found [here](http://www.nvnews.net/vbulletin/showthread.php?t=47405) (official)... It's worth a try,  especially because I run the 6629 one now (7167 gave me segmentation faults after a while, so I couldn't launch new X-software...)

**UPDATE:** I'm now running the 7174 drivers. Moving windows still sucks CPU, but a maximied terminal running top make xorg take 3.6% CPU when I dont press anything for a while. (It did went as low as 2.7%, but that was just for a very short time.)
Glxgears gives me about 200 fps more than running in the normal window, and about 20 fps more when it's maximized. Impressive, some improvement has been made (it could be WAY better, though). Lets just hope I don't get the segmentation faults again...

**UPDATE #2:** Whoah! I ran glxgears again after posting the above, and I got up to ~1030 fps when running in a window (previous: ~800). The maximized window rate is still the same (~90), though.

**UPDATE #3:** I have now been running the new drivers for some hours (working time), and they haven't made any segmentation faults yet... Although, I haven't run any 3D games either... (I think that's what makes it start...)

---

### Post by Dracontopes on 2005-04-01
[QUOTE=MiddleBrooker]HI,
sorry but in this thread seems that the probles is only on Nvidia graphics cards, but actually I've an AMD 64bit with Nforce3 Mainboard and a RADEON 9800PRO by Hercules, so the resizing of a gnome terminal on my desktop take the 100% of CPU!

Thanks for all the HELP!!! ...... and HELP PLEASE!!!
This problem is driving me MAD!!!

Best Regards,

MiddleBrooker[/QUOTE]

Read the thread again :) It has been said several times that it's NOT only a nvidia problem, Ati is affected also. It seems that the problem is xorg/gtk related...

---

### Post by Firetech on 2005-04-04
Nothing new from you guys?

I checked around some more about this problem, and it seems to affect only nvidia and ATI cards... However, I found something in Rage3D's forum about the xaa x-module (XFree86 Acceleration Architecture), but enabling it didn't help.
In another thread of this forum ([link](http://ubuntuforums.org/showthread.php?t=22379) ), someone said he had no problems when he ran xfce instead of gnome (this was an ATI guy), have anyone with nvidia tried this? Anyone with ATI that doesn't agree?
For you people running ATI cards, it seems that running with the "radeon" driver instead of "fglrx" improves 2D performance ([link with more info](http://www.rage3d.com/board/showthread.php?t=33804032)).

What data do you people get if you run "x11perf -copypixpix500" (It seems to be installed by default, I can't recall installing it and I have it.)

My data follows: (I'm running the nvidia driver 1.0-7174)
```
x11perf - X11 performance program, version 1.5
The X.Org Foundation server version 60802000 on :0.0
from Barbaque
Mon Apr  4 16:31:26 2005

Sync time adjustment is 0.2106 msecs.

   8000 reps @   1.1434 msec (   875.0/sec): Copy 500x500 from pixmap to pixmap
   8000 reps @   1.0178 msec (   982.0/sec): Copy 500x500 from pixmap to pixmap
   8000 reps @   1.0124 msec (   988.0/sec): Copy 500x500 from pixmap to pixmap
   8000 reps @   1.0092 msec (   991.0/sec): Copy 500x500 from pixmap to pixmap
   8000 reps @   1.0092 msec (   991.0/sec): Copy 500x500 from pixmap to pixmap
  40000 trep @   1.0384 msec (   963.0/sec): Copy 500x500 from pixmap to pixmap
```
This is a little bit lower values than a guy on Rage3D's forum got when using the fglrx driver (he had about 1.5 msec)... When he used the radeon driver, his values were constant at 0.2014 msec (see the second thread i linked above).

***Edit:*** My bad, it's the XXXX/sec values we're after, the number of reps changes. The guy on Rage3D's forum got well over 4000 reps (or whatever it is) /sec.

---

### Post by JGJones on 2005-04-04
Here's what I got.

```
x11perf - X11 performance program, version 1.5
The X.Org Foundation server version 60802000 on :0.0
from hobbit
Mon Apr  4 17:17:01 2005

Sync time adjustment is 0.0702 msecs.

   3600 reps @   1.2682 msec (   789.0/sec): Copy 500x500 from pixmap to pixmap
   3600 reps @   1.1256 msec (   888.0/sec): Copy 500x500 from pixmap to pixmap
   3600 reps @   1.1262 msec (   888.0/sec): Copy 500x500 from pixmap to pixmap
   3600 reps @   1.1268 msec (   887.0/sec): Copy 500x500 from pixmap to pixmap
   3600 reps @   1.1702 msec (   855.0/sec): Copy 500x500 from pixmap to pixmap
  18000 trep @   1.1634 msec (   860.0/sec): Copy 500x500 from pixmap to pixmap

```

Can you explain what it does and what should we expect? I've got higher times than you so I assume we should be getting 0.2014 or thereabouts?

---

### Post by xander on 2005-04-04
[QUOTE=JGJones]Thanks to that suggestions I've learnt a wee bit ;)


```
 nvidia: module license 'NVIDIA' taints kernel.
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-6629  Wed Nov  3 13:12:51 PST 2004
```

if not then run the dmesg command again without grep and at end of that long list of text you would get a line saying the NVRM failed to load, AGPGART already loaded! - this mean it wasn't blacklisted properly - make sure you blacklist your chipset specific agp part as well.
[/QUOTE]

First:
My glxgears are slower than with AGPART. 

Why?

Second: When I use RenderAccel option, my system freezes while I using mozilla or gedit.

What to do?

Xander

---

### Post by subjectdenied on 2005-04-04
and i thought i was alone with this problem, my system too freezes with the renderaccell-option activated. every time it happens i was scrolling in an application like firefox or openoffice.

i noticed that this happens since the 6611 release of the nvidia-binary-drivers and it's not ubuntu related, cause it happens with the drivers from the nvidia-site too

---

### Post by Dracontopes on 2005-04-04
In Ubuntu, there is no **radeon** driver, but the driver's name is **ati**.

When running X with ati drivers, these results are achieved:

 ```
chris@chris:~ $ x11perf -copypixpix500
x11perf - X11 performance program, version 1.5
The X.Org Foundation server version 60802000 on :0.0
from chris
Mon Apr  4 19:09:10 2005

Sync time adjustment is 0.0367 msecs.

  24000 reps @   0.2395 msec (  4170.0/sec): Copy 500x500 from pixmap to pixmap
  24000 reps @   0.2396 msec (  4170.0/sec): Copy 500x500 from pixmap to pixmap
  24000 reps @   0.2396 msec (  4170.0/sec): Copy 500x500 from pixmap to pixmap
  24000 reps @   0.2395 msec (  4170.0/sec): Copy 500x500 from pixmap to pixmap
  24000 reps @   0.2396 msec (  4170.0/sec): Copy 500x500 from pixmap to pixmap
 120000 trep @   0.2396 msec (  4170.0/sec): Copy 500x500 from pixmap to pixmap

``` 

A lot faster then with **fglrx** driver I think.

---

### Post by xander on 2005-04-04
When I run top I see two procesess called gdm?

Is that normal?

Xander

---

### Post by fackamato on 2005-04-04
```
fackamato@fackamato:~ $ x11perf -copypixpix500
x11perf - X11 performance program, version 1.5
The X.Org Foundation server version 60802000 on :0.0
from fackamato
Mon Apr  4 20:29:26 2005

Sync time adjustment is 0.0443 msecs.

  12000 reps @   0.4454 msec (  2240.0/sec): Copy 500x500 from pixmap to pixmap
  12000 reps @   0.4410 msec (  2270.0/sec): Copy 500x500 from pixmap to pixmap
  12000 reps @   0.4425 msec (  2260.0/sec): Copy 500x500 from pixmap to pixmap
  12000 reps @   0.4429 msec (  2260.0/sec): Copy 500x500 from pixmap to pixmap
  12000 reps @   0.4401 msec (  2270.0/sec): Copy 500x500 from pixmap to pixmap
  60000 trep @   0.4424 msec (  2260.0/sec): Copy 500x500 from pixmap to pixmap

```

With the nVidia driver 1.0-7174. I have a GeForce3 Ti200, using AGPGART on an i875 chipset.

---

### Post by Firetech on 2005-04-04
Actually, I don't know what x11perf does, all I know is that the "msec" numbers should be small... (I asked because I wanted to know if we were on the same level, which we apparently are... The "top test" isn't very accurate, this should be...)
Although, the numbers I think we should compare is the "(XXXXX/sec)", because I see now that some of you got different "reps". Those numbers should be as high as possible (DUH).
The problematic setups apparently lies at about 800-1000 reps/sec. Non-problematic (with acceleration) lies above at least 2000. (You can se more results (ATI) [here](http://www.rage3d.com/board/showthread.php?t=33804032).)

**Xander,**
1: How much slower, as slow as it would be without aceleration? It may be because NvAGP doesn't support your chipset correctly.
2: Run without RenderAccel... For me it does no difference.
3: I also have dual gdm's, so I guess it's normal...

**Dracontopes,** there are both ati and radeon in XFree86 (i think), both are at least shipped with Knoppix...

**fackamoto,** is your system sluggish? what happens when you move windows? (considering CPU usage) What CPU usage does top in a maximized terminal window show?

***Edit:*** I Found some more info about x11perf [here](http://www.xfree86.org/4.2.0/x11perf.1.html) (Actually, that's just the manpage about it...) The x11perfcomp there seems interresting... I'll look into it tomorrow. (It's about 10:30 pm here, and I have school tomorrow...)

---

### Post by fackamato on 2005-04-04
**Firetech**: 3.3% xorg usage in maximized terminal. Moving around windows = >60% usage. Sluggish? Yes, most of the time.

---

### Post by poofyhairguy on 2005-04-04
[QUOTE=Firetech]
For you people running ATI cards, it seems that running with the "radeon" driver instead of "fglrx" improves 2D performance ([link with more info](http://www.rage3d.com/board/showthread.php?t=33804032)).[/QUOTE]


Great link. Too bad, I'd just learned how to get the ATI drivers to work!

---

### Post by jonny on 2005-04-04
[QUOTE=subjectdenied]and i thought i was alone with this problem, my system too freezes with the renderaccell-option activated. every time it happens i was scrolling in an application like firefox or openoffice.[/QUOTE]Yeah, me too.  I left renderaccell enabled today after some tinkering last night.  My son's off school and he's trying to create some web pages.  Guess what?  He had to reboot 6 times in an hour and then started Windows in disgust.  The big question is whether I confess or blame a faulty update from ubuntu...

---

### Post by Firetech on 2005-04-05
[QUOTE=fackamato]**Firetech**: 3.3% xorg usage in maximized terminal. Moving around windows = >60% usage. Sluggish? Yes, most of the time.[/QUOTE]
Strange, your values were a lot higher... Try running "x11perf -move" (takes about 5 minutes) and post the average (last) value for 200 kids. My value is 8210.0/sec.
I guess this depends a lot on the components of the system... What CPU do you got?
I have a "P4" Celeron 2.4 GHz (128kb cache).

[QUOTE=poofyhairguy]Great link. Too bad, I'd just learned how to get the ATI drivers to work![/QUOTE]
You mean you got the fglrx driver to work?

[QUOTE=jonny]Yeah, me too. I left renderaccell enabled today after some tinkering last night. My son's off school and he's trying to create some web pages. Guess what? He had to reboot 6 times in an hour and then started Windows in disgust. The big question is whether I confess or blame a faulty update from ubuntu...[/QUOTE]
Strange, my computer doesn't do anything different with RenderAccel on... There seems to be a lot of sub problems to this problem... The whole thing is a bit strange... Which driver version are you running?

---

### Post by jonny on 2005-04-06
Yet another new nvidia driver has appeared in the repositories - don't these developers ever sleep? - but I've not yet tested performance.  Instead, I wanted to see how a gnome application performed on a different software stack.

I've just tested top running in gnome-term on FreesBIE under XFCE.  Heck, this software is fast.  Running top in a maximised window at 1280x768 with the nv driver, Xorg, and Gnome 2.8 (albeit via an XFCE desktop), Xorg averages 0.03% of CPU (yes, the decimal point is in the right place) - that's 300 times more efficient than Hoary on the same machine!  Everything feels fast and snappy, and this is an ancient PC that I'm using.

If GTK apps can fly under BSD, why not under Linux?  Are there any software developers out there who understand this issue?

By the way, I seriously recommend FreeSBIE.  It includes some great, ahem, unadulterated multimedia applications.  And it's FAST.  I might just find a spare disk partition for a permanent install.

---

### Post by MiddleBrooker on 2005-04-07
Hi to all,
I can't belive that this problem isn't already fix!

I've tried a simple OpneGL visual effect builtin with Xmms and the CPU go immediately up to 100% , resizing an Aterm terminal with only a fade effect take the 100%PU too.

The only thing is attend a fix or upgrade by Ubuntu?
At this point I'm thinking to install the classical xserver-xfree86 and see if there're any changes! -----> Any suggestion about this choice?

I would like to have a little summary about the problem, because some people had found a fix through 

- dist-upgrade 
- some people with the agpgart module blacklisted 
- other people by killing powernowd
- other people by switching Depth from 24 to 16 (*)

(*) Fglrx doesn't support Depth to 16 !


So if someboady can explain the status of dvelopmet I'll be very happy to know this.

Thanks for all the support.

MiddleBrooker

---

### Post by JGJones on 2005-04-07
[QUOTE=jonny]Yet another new nvidia driver has appeared in the repositories - don't these developers ever sleep? - but I've not yet tested performance.  Instead, I wanted to see how a gnome application performed on a different software stack.

I've just tested top running in gnome-term on FreesBIE under XFCE.  Heck, this software is fast.  Running top in a maximised window at 1280x768 with the nv driver, Xorg, and Gnome 2.8 (albeit via an XFCE desktop), Xorg averages 0.03% of CPU (yes, the decimal point is in the right place) - that's 300 times more efficient than Hoary on the same machine!  Everything feels fast and snappy, and this is an ancient PC that I'm using.

If GTK apps can fly under BSD, why not under Linux?  Are there any software developers out there who understand this issue?

By the way, I seriously recommend FreeSBIE.  It includes some great, ahem, unadulterated multimedia applications.  And it's FAST.  I might just find a spare disk partition for a permanent install.[/QUOTE]

If you say that Gnome flies using XFCE as the windows manager, in Ubuntu, they use metacity as the window manager - would it be that metacity is the one making xorg use a lot of CPU?

I've no idea how to set up Gnome so that it use XFCE as the windows manager in Ubuntu to test that but you can get XFCE in Ubuntu via Synpatic I think.

If anyone can change the windows manager from Metacity to XFCE and report on the xorg usage that would be good.

---

### Post by JGJones on 2005-04-07
Reposted as bug @

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8756](https://bugzilla.ubuntu.com/show_bug.cgi?id=8756)

---

### Post by daniels on 2005-04-07
To all of you, have you all checked that the nvidia kernel module is loaded (et al)?  As I've said before, I think there are many issues all being conflated here, and one of them is just incorrect configuration of binary drivers, leading to no acceleration, meaning that the CPU does all the work.

The other issues here would be a) fglrx just isn't great at 2D acceleration, b) powernowd fun, and c) issues in the binary drivers such as the ones seen lately (if upgrading from 6629 -> 7167 fixed your problem, then it was a bug in the nVidia drivers and in no way was Ubuntu ever even partially responsible; ditto if 6629->7167/7174 breaks anything).

---

### Post by fackamato on 2005-04-07
[QUOTE=daniels]To all of you, have you all checked that the nvidia kernel module is loaded (et al)?  As I've said before, I think there are many issues all being conflated here, and one of them is just incorrect configuration of binary drivers, leading to no acceleration, meaning that the CPU does all the work.

The other issues here would be a) fglrx just isn't great at 2D acceleration, b) powernowd fun, and c) issues in the binary drivers such as the ones seen lately (if upgrading from 6629 -> 7167 fixed your problem, then it was a bug in the nVidia drivers and in no way was Ubuntu ever even partially responsible; ditto if 6629->7167/7174 breaks anything).[/QUOTE]

Hehe yup, everything's correct set up, at least here. Using the 71.74 nvidia module, glxgears gives me 2300fps on my GeForce 3 Ti200, scrolling in FireFox etc is smooth, but moving around a window shows >50% cpu usage most of the time (if it's a big window). And a fully maximized terminal, with just top running, shows xorg using 3 to 4 percent of the cpu. Doing nothing, except updating top stats...

---

### Post by dermotti on 2005-04-07
Ditto with above, cept im using kubuntu, and it still says ot takes alot of CPU power when moving windows, but i dont visually see any slow downs.

---

### Post by MiddleBrooker on 2005-04-07
[QUOTE=daniels]To all of you, have you all checked that the nvidia kernel module is loaded (et al)?  As I've said before, I think there are many issues all being conflated here, and one of them is just incorrect configuration of binary drivers, leading to no acceleration, meaning that the CPU does all the work.

The other issues here would be a) fglrx just isn't great at 2D acceleration, b) powernowd fun, and c) issues in the binary drivers such as the ones seen lately (if upgrading from 6629 -> 7167 fixed your problem, then it was a bug in the nVidia drivers and in no way was Ubuntu ever even partially responsible; ditto if 6629->7167/7174 breaks anything).[/QUOTE]

Sorry Daniels,

please can you tell me some information about this problem related to the fglrx driver?
You've spoke about nvidia case, but what about ATI?

Thank you very much!!

---

### Post by daniels on 2005-04-07
If upgrading between different fglrx versions fixes your problems, then fglrx is the culprit.  fglrx is also quite bad at 2D acceleration.

---

### Post by nojjy on 2005-04-08
I am still not seeing any improvement at all after following all of the suggestions on this thread.  CPU usage spikes when resizing windows or scrolling in firefox.  I did not have this issue at all when using Slackware 10.1 + Dropline Gnome 2.8.  In fact, using that configuration interactivity was considerably faster and smoother than Windows, but this is definitely NOT the case with Ubuntu Hoary.  Here is my system:

dual Athlon MP 1800
tyan tiger mpx motherboard
1GB RAM
Nvidia Geforce3 Ti200
7200rpm 80g hard drive.

latest ubuntu k7 smp kernel
all ubuntu software up to date.

---

### Post by Firetech on 2005-04-08
Is there any reasons NOT to run a home compiled kernel and nvidia module?
Are the ubuntu nvidia drivers better in any way?
(My vmware vmmon module won't compile without a compiled source tree)

---

### Post by bassMonkey on 2005-04-09
I have no idea if this works but put this into the "Device" section in your xorg.conf:

```
 Option          "RenderAccel"           "true"
```

---

### Post by Dracontopes on 2005-04-09
ATI Proprietary Linux x86 Drivers for XFree86 / X.Org Version   8.12.10

New drivers for ATi I think. Gonna try them now :-) ^_^

**Edit:** No improvement. Windows still sluggish. Xorg @ 80% load when moving windows.

---

### Post by Firetech on 2005-04-09
[QUOTE=bassMonkey]I have no idea if this works but put this into the "Device" section in your xorg.conf:

```
 Option          "RenderAccel"           "true"
```[/QUOTE]
If you've read the whole thread, you would see that this has been suggested before, and that it, sadly, doesn't help...

---

### Post by p!=f on 2005-04-09
[QUOTE=Firetech]Is there any reasons NOT to run a home compiled kernel and nvidia module?
Are the ubuntu nvidia drivers better in any way?
(My vmware vmmon module won't compile without a compiled source tree)[/QUOTE]
If your custom kernel works fine why not to run it? :) You may be missing some patches presented in the "stock" Ubuntu kernel, though.
Ubuntu nVidia packages contains some patches and tweaks not found in the nVidia installer so I recommend to use them instead.
If you want to compile vmmon under Ubuntu kernel you need to install kernel-headers for your kernel / achitecture.

---

### Post by p!=f on 2005-04-09
[QUOTE=Dracontopes]ATI Proprietary Linux x86 Drivers for XFree86 / X.Org Version   8.12.10

New drivers for ATi I think. Gonna try them now :-) ^_^

**Edit:** No improvement. Windows still sluggish. Xorg @ 80% load when moving windows.[/QUOTE]
Do you experience same issues under other desktop environment? (KDE, XFCE4, ...)

---

### Post by jonny on 2005-04-09
Haven't tried XFCE on Ubuntu, but KDE is just as bad when running gnome applications (eg gnome terminal).  KDE apps (eg konsole or konqueror) fly.

Interestingly, as I noted a few posts ago, gnome terminal is extremely snappy in the XFCE desktop environment under BSD.  It's also significantly less slow - but still fairly poor - in other linux distros.

---

### Post by WMCoolmon on 2005-04-10
I've tried the RenderAccel options and such; I haven't tried blacklisting agpgart, because it seems as though the NVIDIA driver *is* loading.

Stats:
AMD64 2800+
512 MB DDR400
GF6600GT
MSI-K8MM-ILSR motherboard

The amount of slowdown also seems dependant on the skin that I use.

Hope that helps the dev team; it's not exactly unbearable, but it is sort of annoying.

---

### Post by Firetech on 2005-04-10
[QUOTE=p!=f]If your custom kernel works fine why not to run it? :) You may be missing some patches presented in the "stock" Ubuntu kernel, though.[/QUOTE]I compiled it using the linux-source package, which contains the Ubuntu patches. (According to the package description at least...)

[QUOTE=p!=f]Ubuntu nVidia packages contains some patches and tweaks not found in the nVidia installer so I recommend to use them instead.[/QUOTE]Impossible if I use my own kernel, it didn't work when I tried at least...

[QUOTE=p!=f]If you want to compile vmmon under Ubuntu kernel you need to install kernel-headers for your kernel / achitecture.[/QUOTE]Didn't work. vmware-config.pl requires a compiled kernel tree containing some directories that are created during compilation (and that doesn't come with linux-headers). I couldn't recompile the original kernel using the headers either.

---

### Post by p!=f on 2005-04-10
[QUOTE=Firetech]
Impossible if I use my own kernel, it didn't work when I tried at least...
[/quote]
It didn't work mean exactly? :)
Two Debian ways to create a nvidia-kernel package for your kernel:
1.
```

sudo apt-get install nvidia-kernel-source module-assistant fakeroot
sudo module-assistant
sudo ln -s /usr/src/<your_linux_sources> /usr/src/linux

```
(fakeroot and symlinking is optional)
-> UPDATE, PREPARE, SELECT -> pick nvidia-kernel -> GET -> BUILD and finally install the package
2. 
```

sudo apt-get install kernel-package
sudo make-kpkg --initrd --config=menuconfig --revision=1 --added_modules=nvidia-kernel kernel_image modules_image

```
Note that --revision and --added_modules are optional. --initrd is recommended. You also need to unpack nvidia-kernel-source first.
Both kernel and nvidia-kernel packages will be created.

---

### Post by WMCoolmon on 2005-04-10
I've been trying to get a custom kernel working, but X is unable to start (and so far the keyboard doesn't seem to work either).

Is there anything special I need to do to get the nvidia driver working with a custom kernel? I followed the instructions in the KernelByHandHowTo wiki entry.

I'm hoping that this will solve some of the speed problems, as at least one user was able to speed up their Gnome via a custom kernel.

---

### Post by fackamato on 2005-04-10
[QUOTE=WMCoolmon]I've been trying to get a custom kernel working, but X is unable to start (and so far the keyboard doesn't seem to work either).

Is there anything special I need to do to get the nvidia driver working with a custom kernel? I followed the instructions in the KernelByHandHowTo wiki entry.

I'm hoping that this will solve some of the speed problems, as at least one user was able to speed up their Gnome via a custom kernel.[/QUOTE]

Yeah, you have to rebuild the nvidia module. Just apt-get remove it, and download it from the nvidia site and install. Nothing fancy.

---

### Post by WMCoolmon on 2005-04-10
Thanks, I'll try that. :-)

---

### Post by p!=f on 2005-04-11
[QUOTE=WMCoolmon]I've been trying to get a custom kernel working, but X is unable to start (and so far the keyboard doesn't seem to work either).

Is there anything special I need to do to get the nvidia driver working with a custom kernel? I followed the instructions in the KernelByHandHowTo wiki entry.

I'm hoping that this will solve some of the speed problems, as at least one user was able to speed up their Gnome via a custom kernel.[/QUOTE]
Read my post above.

---

### Post by p!=f on 2005-04-11
[QUOTE=fackamato]Yeah, you have to rebuild the nvidia module. Just apt-get remove it, and download it from the nvidia site and install. Nothing fancy.[/QUOTE]
No no no. :) There's no need to download it from nvidia site (unless there's a newer version you have to run) when you have a possibility to install it from patched Ubuntu sources. There's also no need to remove your current module from the system. As soon as you compile your custom kernel + nvidia module, it won't interrupt with the current one.

---

### Post by cudjoe on 2005-05-09
13 pages to examine on this thread...thousands of combinations to attempt without crashing the system, kernel or whatever driver is really tough !

I've tried almost everything I read so far and GUI is still sluggish ! 3D graphics are nice and smooth, but web browsing or usual 2D apps are deadly slow. 
I found a lot of bugtracks and threads on Nvidia, Gnome and Xorg websites...
Did anybody find a link to keep an unified eye on this velocity problem ?

Do you think that there would be **a** way to the solution ? Could we summarize somewhere (wiki?) what did actually worked and which parts of the system are worth to crumble ?
What about the [Xorg test suite](http://www.x.org/XOrg_Press_Releases/XTS5.0.2.html), we could all compare results and profiles ?

That's a pity because I've been advertising Ubuntu for a long time and I must confess that I receive plenty of complains from my flatmates ! I look forward to the patches !

---

### Post by krusbjorn on 2005-05-09
I dont know if anyone else experienced this, but removing powernowd didnt make resizing windows better, but moving around windows and scrolling in firefox hardly take any cpu speed at all now.

---

### Post by Pirate_Will on 2005-05-28
This is a big problem for me and has caused me to switch to Kubuntu and more recenlty onto Fedora. I really much prefer Ubuntu to Fedora and Kubuntu, but until this problem gets sorted I won't be returning. 

I would also like this subject to be summarised somehow, I tried most of the suggestions in this thread to no avail, and have returned time and again in the hope of a solution being posted. I agree with cudjoe, 13 pages is a lot of material especially with the links to bugzilla, so could someone PLEASE do something about this, a wiki page anything PLEASE.

---

### Post by sard on 2005-06-04
So glad I found this thread!  Just installed 5.04 and am getting the horribly slow redraw rate when I move windows etc.  Looks like everything is being done by the CPU instead of the gfx card.

Messing with video drivers made no difference.  Not sure how the devs managed not to notice this problem.  I'm going to give Kubuntu a go to see if it's any better.

---

### Post by Dax0r on 2005-06-13
I've the same problem....Xorg,after a general upgrade,become a cpu hog(10-15%)!
I have a Ati card,I've tried to compile my own kernel but Xorg take always a lot of CPU resources...I havent cpu scaling  :-?

---

### Post by deleric on 2005-06-13
[QUOTE=Biffy]Hello? Where did everyone go? Did turning off powernowd help for all of you? Cause it didnt help at all here.[/QUOTE]

sure helped!

---

### Post by fackamato on 2005-06-13
[QUOTE=deleric]sure helped![/QUOTE]

Are you using a laptop? If so, that makes perfect sense.

---

### Post by cudjoe on 2005-06-22
...I'm still struggling with this problem...

I found an [advanced description of the problem](http://www.ii.uib.no/~ketil/ubuntu-prob.log), which suggests to switch CPU scaling from *powersave * to *perfomance*. I'll try that as soon as I get home.

```
#!/bin/sh

SYSFS_CF_GOVERNOR="/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"

case "$1,$2" in
(change,power)
        if on_ac_power >/dev/null; then
                echo -n "performance" > "${SYSFS_CF_GOVERNOR}"
        else    
                echo -n "powersave" > "${SYSFS_CF_GOVERNOR}"
        fi
        ;;
esac
```

---

### Post by cudjoe on 2005-06-23
I have realized that I actually was looking at laptop stuff...whereas I got a good old immobile machine !

...that may explain why I don't have any *powernowd * process nor *cpufreq/scaling_governor * directory.

Is there anybody around here, that found a solution ? or even an awkward trick ?

...I don't really like KDE, but if it is the only alternative then I'll look at it...

Thanks dudes

---

### Post by keebler on 2005-07-14
Just to recap, it looks like the problem is GTK using the render extension for font antialiasing.  It is NOT strictly an nvidia problem, powernowd has nothing to do with it, and color depth probably doesn't matter either.  If you don't mind grainy fonts, you can disable antialiasing and the problem goes away.

In the gnome menu, go to System->Preferences->Font  and set "Font Rendering" to "Monochrome".  It's ugly, but it works.

---

### Post by markoz on 2005-07-15
[QUOTE=keebler]Just to recap, it looks like the problem is GTK using the render extension for font antialiasing.  It is NOT strictly an nvidia problem, powernowd has nothing to do with it, and color depth probably doesn't matter either.  If you don't mind grainy fonts, you can disable antialiasing and the problem goes away.

In the gnome menu, go to System->Preferences->Font  and set "Font Rendering" to "Monochrome".  It's ugly, but it works.[/QUOTE]

What you said isn't true for me keebler. So far I tryed everthing suggested in the posts but nothing worked. Have a PIII 933 MHz, Gforce2 card etc.
Still whenever I resize a window, espetialiy gnome terminal, the cpu goes to 99%. It is a little better with xterm. Resizeing xterm brings the cpu up to 45-50% only.

---

### Post by Teroedni on 2005-07-31
Heh its the same here to
When i change windows or resize the cpu 3 to 4 times goes up to 80% AMD 2600
My AMD Barton use only 60% but it is also overclocked to a 3000+
I didnt realise this before i read this tread as it has never plagured me :-P 

For the unlucky out there who have bigger problems than me . Have you tried reformating and new install. I can often help a lot;)

---

### Post by deleric on 2005-08-02
[QUOTE=fackamato]Are you using a laptop? If so, that makes perfect sense.[/QUOTE]


yep, a Dell Inspiron 8600.

---

### Post by bubblegum on 2005-08-09
[QUOTE=keebler]Just to recap, it looks like the problem is GTK using the render extension for font antialiasing.  It is NOT strictly an nvidia problem, powernowd has nothing to do with it, and color depth probably doesn't matter either.  If you don't mind grainy fonts, you can disable antialiasing and the problem goes away.

In the gnome menu, go to System->Preferences->Font  and set "Font Rendering" to "Monochrome".  It's ugly, but it works.[/QUOTE]

You're right and it's not a surprise. Render is known to be very slow at rendering fonts (pango call Render and pango is not fast  because it is very accurate and handle non western langage very well). Render is somewhat accelerated on nvidia binary driver but it is still a lot slower than it should be. Render is not accelerated at all using the "ati" open source driver (don't know but I believe it is neither with fglrx). In fact we shouldn't expect to see correct Render performance in our lifetime (see Rasterman rants about render being 50x slower than it could be). 
The solution is when the desktop will be drawn using cairo + glitz (opengl hardware acceleration) but it's still a long way off and I believe it'll take some time to be optimized and reliable.

 Why QT font rendering (does not use pango IIRC, but uses Render) feel a lot faster I don't know, because it uses less render features maybe.

So just setting font rendering to monochrome make font rendering a lot faster and the desktop smoother (compare scrolling in firefox with monochrome vs other antialias modes). It's still slower than it should be.

Monochrome rendering is hideous so a solution is to use non AA at standard font size using a high quality font like tahoma or verdana or arial with the freetype bytecode interpreter enbaled to have great rendering (nearly matching windows). See [article](http://ubuntuforums.org/showthread.php?t=20976&highlight=DisplaySize)

Edit: I followed the linked article (not using tahoma but Arial) + the following ~/.fonts.conf to disable AA at standard font size that allow to have excellent font rendering using the "monochrome" font settings in gnome font properties panel (and thus disabling the slow ass Render AA for common font size):

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>bgr</const>
  </edit>
 </match>
 <match target="font" >
  <test compare="more" name="size" qual="any" >
   <double>8</double>
  </test>
  <test compare="less" name="size" qual="any" >
   <double>12</double>
  </test>
  <edit mode="assign" name="antialias" >
   <bool>false</bool>
  </edit>
 </match>
 <match target="font" >
  <test compare="more" name="pixelsize" qual="any" >
   <double>10</double>
  </test>
  <test compare="less" name="pixelsize" qual="any" >
   <double>15</double>
  </test>
  <edit mode="assign" name="antialias" >
   <bool>false</bool>
  </edit>
 </match>
</fontconfig>


With all this, Xorg cpu usage is 1% for a full maximized gnome-terminal (1440x900) 
(screenshot in following post)

Follows another showing font rendering quality in firefox: whose scrolling is very smooth

---

### Post by bubblegum on 2005-08-09
[IMG]http://bubbleguuum.free.fr/ubuntu/terminal.png[/IMG] 

[IMG]http://bubbleguuum.free.fr/ubuntu/firefox.png[/IMG]

---

### Post by nom on 2005-08-13
heya having exactly the same problem here. I have blacklisted agpgart, tryed almost everything mentioned here including changing fonts with no luck cpu usage is going upto about 40% when moving windows / watching videos :(

my xorg.conf
```
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
	Option 		"NvAGP" 		"1"
EndSection
```

lspci
```
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 655 Host (rev 50)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f1 (rev a2)
```

dmesg
```
nvidia: module license 'NVIDIA' taints kernel.
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
```

and finally glxgears to show the sevirty of it while moving around some windows.
```
31669 frames in 5.0 seconds = 6333.800 FPS
14399 frames in 5.0 seconds = 2879.800 FPS
1658 frames in 5.0 seconds = 331.600 FPS
1542 frames in 5.0 seconds = 308.400 FPS
23055 frames in 5.0 seconds = 4611.000 FPS
31363 frames in 5.0 seconds = 6272.600 FPS
```

running a fresh Hoary 5.04 install on a p4 3.0 with a 6600GT any help would be GREATLY appreciated want to get this running smooth asap =]

cheers, nom.

---

### Post by Pikapooh on 2005-08-16
Same problem here, with Ubuntu 5.04 and ATI 320M. Maybe Gnome isn't *so* sluggish, but CPU usage is very high.

When I run top in terminal, and do nothing, CPU usage is 1,5%-2,5%. Not so bad, but when I try to move mouse cursor (not drag window or smth, just move) usage jumps to 10-30%!. Scrolling windows in Opera takes 40%, moving windows up to 100%. Not nice.

So, sadly,  the problem is real and affect many ppl here :/.

*Edit:*
Disabling powernowd didn't help. Adding RenderAccel to xorg.conf neither (does it work with ATI cards, anyway?).

---

### Post by GoA on 2005-08-17
Ok, same problem here. I'm using Kubuntu with KDE 3.4.2 And linux-kernel-686. My system specs are Athlon 2800@2200 MHz, 1 Gb ram, 80 gig hd, matrox g400 adapter. I haven't installed matrox own drivers but I added som information in to the xorg.conf, such as agp 4x and fast write. I also changed the default bitdepth to 16. I removed also powernowd. Windows are still slow and for example moving terminal over firefox windows takes about 100 % of cpu speed...

---

### Post by bonovoxpsu on 2005-08-17
[QUOTE=Pikapooh]Same problem here, with Ubuntu 5.04 and ATI 320M. Maybe Gnome isn't *so* sluggish, but CPU usage is very high.

When I run top in terminal, and do nothing, CPU usage is 1,5%-2,5%. Not so bad, but when I try to move mouse cursor (not drag window or smth, just move) usage jumps to 10-30%!. Scrolling windows in Opera takes 40%, moving windows up to 100%. Not nice.

So, sadly,  the problem is real and affect many ppl here :/.

*Edit:*
Disabling powernowd didn't help. Adding RenderAccel to xorg.conf neither (does it work with ATI cards, anyway?).[/QUOTE]
 please read page 14 - it appears it has a lot to do with the AA of fonts and font rendering.  i will try this possible solution tonight.

---

### Post by JoeUbuntu on 2005-08-17
Same problem as most in this thread. Scrolling in a firefox window, or moving windows takes cpu usage up to 100%. 

I am running an Athlon XP 2200+, 512mb ram, ATI Radeon 9200, with a clean ubuntu install. 3d acceleration is working fine on my ATI card, so I'd agree with the general consensus - it seems to be a 2d rendering bug. Not like I know much!

---

### Post by bonovoxpsu on 2005-08-18
[QUOTE=JoeUbuntu]Same problem as most in this thread. Scrolling in a firefox window, or moving windows takes cpu usage up to 100%. 

I am running an Athlon XP 2200+, 512mb ram, ATI Radeon 9200, with a clean ubuntu install. 3d acceleration is working fine on my ATI card, so I'd agree with the general consensus - it seems to be a 2d rendering bug. Not like I know much![/QUOTE]
 we need some more feedback here.  i dropped off font scaling and it looks absolutely horrible...  not to mention i didn't see a change in performance...

---

### Post by Envel on 2005-08-23
The bug is not exist with ATI drivers from dri-project (ATI radeon 9000 Pro). 2D perfomance is much better with this card than with Radeon 9600 and fglrx driver.

---

### Post by Pikapooh on 2005-08-24
Where I can download latest ati dri drivers? Is [http://dri.sf.net/](http://dri.sf.net/) correct address? I heard that dri for Xorg is currently maintained by Xorg folks, but I wasn't able to find any downloadable stuff on their site.

Can u provide some howto about downloading and installing (compiling?)? It would be really great. ATM I don't even have DRI enabled at all, so can't play 3d games :]

---

### Post by prelude on 2005-09-16
this 'thing' exists in breezer aswell.

allthough I get great (from what I can understand) testresults in x11perf with option -copypixpix500 (results below) Im suffering with high cpu usage and slow, jerky updates when moving and resizing windows yet scrolling in firefox is smooth. the biggest annoyance to me with this is when I move a window copies of it stays on the background for as long as 0.5 seconds, when this happens xorg usually uses 70%.
resizing a terminal window does xorg use 60% cpu, but resizing a firefox window does xorg use 30% and firefox 70%(?) cpu, while scrolling in a firefox window cpu the cpu usage of xorg is in the 30's when doing that.

Ive tried setting the fonts to monocrome (with the font control panel, not manually) but that yielded no great diffrence. also, renderaccel on/off in xorg.conf had no notable diffrence. I discovered that I was running powernowd, stopping it and uninstalling it also had no effects.
what I havent done is try nvidia's agp-module, as my agp-support is static in my kernel. ;)

tech specs.
P4-2.5Ghz, 1.5GB ram, 6600GT, nvidia driver 7667 and custom built 2.6.12 kernel.

```

x11perf - X11 performance program, version 1.5
The X.Org Foundation server version 60802000 on :0.0
from snakes
Fri Sep 16 21:08:12 2005

Sync time adjustment is 0.0377 msecs.

  24000 reps @   0.2224 msec (  4500.0/sec): Copy 500x500 from pixmap to pixmap
  24000 reps @   0.2198 msec (  4550.0/sec): Copy 500x500 from pixmap to pixmap
  24000 reps @   0.2196 msec (  4550.0/sec): Copy 500x500 from pixmap to pixmap
  24000 reps @   0.2192 msec (  4560.0/sec): Copy 500x500 from pixmap to pixmap
  24000 reps @   0.2196 msec (  4550.0/sec): Copy 500x500 from pixmap to pixmap
 120000 trep @   0.2201 msec (  4540.0/sec): Copy 500x500 from pixmap to pixmap

```

---

### Post by b34r on 2005-10-02
Any news regarding this ?
or do i have to send my ubuntu disk out the window ?

---

### Post by Chris Allison on 2005-11-03
Is there any resolution to this problem(s)?  I just recently installed Ubuntu.  Everything is great except for this problem.  Unfortunately, it is a pretty large problem.  Everything seems very sluggish.  Should I try Kubuntu instead?

---

### Post by fackamato on 2005-11-04
[QUOTE=Chris Allison]Should I try Kubuntu instead?[/QUOTE]


***I*** think so. I did, and I will never go back to gnome again! KDE is just wonderful.

---

### Post by GrootBrak on 2005-11-23
I found this thread after much searching about getting frame rate up.
Whoever said things was/is connected to video card or settings have it way wrong. I have an Intel 915 chipset. My graphics originally was a bit slow. After I changed my xorg.conf file a bit I got it working pretty well.
I upgraded from Warty to Hoary to Breezy. No problems. A week or so ago my kids complained their games was slow. Now they do have the tendency of playing everything and not always closing windows, thus slowing things down, I never thought much of it.

Until recently I noticed my games is also jumpy. GLXGEARS start fine for a few seconds and then simply dies down to very slow clicks. So I started another futile search.... My config files is still the same, my hardware is still onboard graphics from Intel etc. The game supertux only play normally when I disable the OpenGL option. All other games is now buggered. Screen savers overheats my PC. (How about CPU savers?!!!) 

During my search I notice a few "Xorgs eats my processor" posts, but I thought thats not my problem. After reading and testing and trying this post, I can say the bugger has to do with Xorg. Unfortunately upgrading to Breezy removed my Kubuntu, darn... so I cannot test the fallback.

But good as this forum may be, as soon as you ask "strange" questions, a deep silence envelopes your post. In the end the only replies you get is babies breastfeeding babies. No gains, no losses, only a waste of time.

I certainly would love to see what the resolve would be, else I will try and fall back to my old kernel, and hopefully that will work.

---

### Post by GrootBrak on 2005-11-24
Fallback to old kernels still suck my CPU dry. I monitored my CPU when starting glxgears. CPU goes from about 1% when opened and then glxgears run fast. As the CPU reaches about 60% it starts slowing down. At 99,7% glxgears is very very slow. Running this small app for more than a minute, my cpu fan runs full blast, and you can actually feel the extra heat out of the air outlet aftre three minutes. So whatever is causing this bug, will also cause early CPU failures. I think this needs URGENT ATTENTION. I never even heard my cpu speeds up before this thing cropped up.

---

### Post by Anonymaus on 2005-11-24
Hi everyone!

I've read all 16 pages now and it looks like most of you guys are using Ubuntu with Gnome.

I'd like to know how many Kubuntu/KDE users are having the same problem.

I'm using Kubuntu with KDE myself. Did a fresh install of Breezy (though my home drive is still the same). Xorg CPU usage is aroung 4% when idling (Konsole open with top running), but sometimes goes up to 20% without any (obvious) reason, not even touching the mouse.
Scrolling in firefox takes the xorg to 40-60%, moving windows around two. This happens with KDE apps too! Tried it with Konsole and with Konqueror scrolling through a directory listing.

Hardware (Athlon64 3000+, 2GB RAM, ATI Radeon 9800, but Kubuntu 32bit though) shouldn't be the problem. Updated to the 2.6.12-10 kernel today, makes no difference.

I know, there are more Ubuntu than Kubuntu users. Is that why most postings are related to Ubuntu or is it because the problem is less common on Kubuntu?

One thing that I'm wondering about is that the CPU usages stays up for some seconds (at least for 2-3 top-refreshes) after I've done something. Is this due to top being a bit late or does Xorg do some unusual things (spawning/destroying threads/processes, grabbing/freeing memory,...)?

**Update:** I've installed Xfce, everything is just fine. CPU usage is between 0 and 1% when idling, goes up to 20% when scrolling around. Could it be that QT/KDE is starting to make the same problems as GTK/Gnome?

**Update2:** Ok, I figured out why the idle usage was so high. It was due to the knewsticker. Idle usage seems normal now. Still, closing a full screen firefox peaked at 89%.

---

### Post by dezier on 2005-11-26
I'm having the same problem running on AMD Athlon XP2000+, 512 RAM, ATI Radeon 9600...

Xorg uses a lot of cpu resources, but i don't have that really sluggy feeling. But what the i heck, i thought, I can't live with this. So I installed XFCE. Did it solve the problem? No! It actually feel a little bit more snappy, but maximizing and minimizing Opera and xorg uses between 8 and 30%. Scrolling 15%, but sometimes up to 100%. Moving xterm window 18%.

Anyone else that face the same problems even using XFCE?

---

### Post by GrootBrak on 2005-11-27
I downloaded and installed KDE, but the cpu is still straining in KDE as well. As I said, I only experienced the slow down weeks after I upgraded to Breezy. I have reason to believe that some of the regular updates through synaptic caused a slow down. I reinstalled Xorg and whatever I think X-org related, but it still fails.

Something that occur to me now. I did one of those "mark all upgrades" in Synaptic just before I had this problem. I recall that the output failed with two things, one to do with Alsa, the other if I recall was Xfree86-common. It complained about package overlap or something worse, I resolved it by removing the suggested two packages, for the life of me I can't remember what it said exactly. Trying to install the package below gets me this result.

> xserver-xfree86:

Package xserver-xfree86 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

BTW I have Intel onboard graphics on a desktop. I allocated 64M to graphics when setting. None of these 16 pages helps got me recaliming any bit of processor back.

---

### Post by Anonymaus on 2005-11-28
Ok, I solved the problem for my box. Xorg still has peaks on some operations but they seem to have no influence on the performance. System runs normal now.

Well, the problem in my case was Taskbar V2. I like eyecandy :rolleyes: so   the screenshot feature was active. It took screenshots of windows every time I minimized, maximized, opened new ones or closed old ones (yes, even when closing Xorg went up). I turned off the screenshot function and everything runs much smoother now.

Don't know if this helps anyone else than myself. Just wanted to mention it :p

---

### Post by TheJoker on 2005-11-30
I'm running KDE on an AMD64 and I had problems with powernowd and solved it. Now I got a new kernel (2.6.12-10-amd64-generic) and the problems have started again. This morning I booted up and I've since left the machine running (not even touched it!)...

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
 7133 root      25   0  308M  108M  2064 R 99.3 14.7  2h29:51 /usr/X11R6/bin/X -br -nolisten tcp

I've got a triple head powered by two nVidia cards, as the new kernel came along I had to recompile the nVidia driver (seems to have worked fine). 

If I do something stressful - such as boot a VMWare machine or rip a CD the computer dies on me... 

Linux didn't use to be this unstable (sure X crashed etc, but seldomly halted the computer)... :rolleyes:

---

### Post by GrootBrak on 2005-12-02
[QUOTE=Anonymaus]
Well, the problem in my case was Taskbar V2. I like eyecandy :rolleyes: so   the screenshot feature was active.[/QUOTE]

Where do you get this from? Is it in Gnome?

---

### Post by Anonymaus on 2005-12-02
[QUOTE=GrootBrak]Where do you get this from? Is it in Gnome?[/QUOTE]

No, Taskbar V2 is a kicker applet. [See here]("http://kde-look.org/content/show.php?content=31611"). I used it because it shows the window list without the button background for every entry. Actually I used to use it as KDE 3.5 window list applet has the 'elegant mode' which does the same.

---

### Post by GrootBrak on 2005-12-12
I have been the good boy and removed Ubuntu completely from my system after copying my setup to another disk. Formatted my HD and reinstalled Hoary from CD.

I activated the minimum apps. Fired up "top" and "glxgears" same problem. I reckon that I was using XFREE86 in stead of Xorg up until I updated everything to Breezy. But I cannot be 100% sure. As I mentioned earlier, I had no problems in the past. The only thing I ever did was to add more Videoram to my xorg.conf file to get my frame rate up.

So I removed Hoary again, copied my old files back, via the installer but now its gone. For some silly flippen reason, I can see the mount point with my back-ups, but the folder is empty. So now my old "saved files" is unsaved. Anyone know I good file recovery program for Linux?!!!

Fed-up, I installed Mandrake 10.0 from CD. Smooth sailing. glxgears runs so fast I can hardly see the spokes of the gears. Frame rate only reported as 512fps. (Don't ask...) My cpu goes right up to 99%, but the video is still smooth. Only later did I realise I still have not added videoram to my xorg.conf file or whatever handles it in Mandrake! Bad news is that Tuxracer is stuttering. Previously in Ubuntu adding videoram solved that issue.

Now the big question. Learn and setup Mandrake or stick with Ubuntu? I filed a bug to Xorg developers, but as yet is waiting for a reply.

---

### Post by nowshining on 2007-09-27
> **JGJones said:**
> Thanks to that suggestions I've learnt a wee bit ;)

This is what you need to do to blacklist the agpgart:

go to terminal

```
 lsmod |grep -i agp
```

That will show the AGP modules in use by your system - agpgart followed by the chipset specific module (in my case it is intel-agp as I have intel chipset so I shall use that)

```
 sudo gedit /etc/hotplug/blacklist 
```

Add the two lines as below:

```
 agpgart
 intel-agp
```

If you have sis chipset you would get sis-agp from the earlier command so replace intel-agp with that for example.

```
 sudo gedit /etc/X11/xorg.conf 
```

and edit your Device section so that it includes the two lines as below:

Option "RenderAccel" "true" - as suggested by Daniel
Option	"NvAGP" "1" - enables the NVAGP module if agpgart not present (which is why you need to blacklist it)

```
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	131072
        Option 		"NoLogo" 		"yes"
	Option 		"RenderAccel" 		"true"
	Option 		"NvAGP" 		"1"

EndSection
```

Reboot your computer

When you have logged in, open terminal again and type in the command:

```
 dmesg |grep -i nvidia 
```

if you did the above successful you should get this output:

```
 nvidia: module license 'NVIDIA' taints kernel.
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-6629  Wed Nov  3 13:12:51 PST 2004
```

if not then run the dmesg command again without grep and at end of that long list of text you would get a line saying the NVRM failed to load, AGPGART already loaded! - this mean it wasn't blacklisted properly - make sure you blacklist your chipset specific agp part as well.

If for some reason blacklisting doesn't work for you, there is a roundabout way - not a recommended way

go to /lib/modules/<your kernel>/kernel/drivers/char/agp and rename agpgart.ko to agpgart.ko.saved

On boot up Linux won't find agpgart.ko and so not load it.

Blacklisting is better since it survivies kernel upgrades.

thanks that worked for me. :) I think - ubuntu Gutsy and it used to show intel_agp and now it just shows  ```
 agpgart                35016  1 nvidia
 
```

---

### Post by nimdasmetsys on 2007-11-16
i was facing same problem with Xorg and i fixed it twice by updating libgnome packages

ap-get install libgnome*:)

---

