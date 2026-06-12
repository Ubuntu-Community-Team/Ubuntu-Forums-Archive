---
title: "Monitor shuts off..."
date: 2006-04-10
forum: General Help
---

### Post by hisjoeness on 2006-04-10
Good Day,

I just installed Breezy from a burned ISO. The installation went fine, but that's when things started to suck. I can boot up the machine, and I get the pretty loading screen, but after it loads, the monitor goes black. Then the monitor powers off. When I hit the power button, the monitor powers on again to a login screen, I have just enough time to enter a few characters before it shuts down.

 I can login to recovery (safe?) mode, I can get into grub just fine.

System Specs:
Bone stock dell 2400 circa '03
P4 2.4Ghz
512 RAM
Some kind of integrated video
meh...

Any help is appreciated.

---

### Post by dcstar on 2006-04-10
[QUOTE=hisjoeness]Good Day,

I just installed Breezy from a burned ISO. The installation went fine, but that's when things started to suck. I can boot up the machine, and I get the pretty loading screen, but after it loads, the monitor goes black. Then the monitor powers off. When I hit the power button, the monitor powers on again to a login screen, I have just enough time to enter a few characters before it shuts down.

 I can login to recovery (safe?) mode, I can get into grub just fine.

System Specs:
Bone stock dell 2400 circa '03
P4 2.4Ghz
512 RAM
Some kind of integrated video
meh...

Any help is appreciated.[/QUOTE]
Possibly detected the wrong video driver, do a forum search on how to edit your xorg.conf files and selecting the VESA driver - you should find some detailed instructions you can use.

---

### Post by Prospero2006 on 2006-04-10
It's definitely the xorg.conf file. I had a similar problem when I bought a 19 inch flat panel. Here's what I did:

open up xorg.conf
find the place where the monitor resolutions are listed. 

```
 Section "Screen"
	Identifier	"screen0"
	Device		"Cirrus"
	Monitor		"Monitor1"
	DefaultDepth	24



	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" 
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" 
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280X1024"
	EndSubSection
EndSection

```

Notice two things:
      -I have default depth set to 24.
      -I have one resolution listed under that depth -1280X1024

I suggest you set your default depth to 8 and list a resolution of 800X600
If that works, move up from there. 

Otherwise, check your drivers.

What kind of video card are you running?

Pros

---

### Post by hisjoeness on 2006-04-11
I played with the xorg.conf file for awhile.. it lets me log in as root but not with sudo... I am running an intel integrated video driver, hard to tell exactly which (the google, she does nothing). Been up all night going through the various iterations for the monitor. I just don't know! ](*,) Hopefully I can get this thing working properly soon, I'm driving the wife nuts workin' on it. Thanks for the replies, fellas.

---

### Post by codejunkie on 2006-04-11
[QUOTE=hisjoeness]I played with the xorg.conf file for awhile.. it lets me log in as root but not with sudo... I am running an intel integrated video driver, hard to tell exactly which (the google, she does nothing). Been up all night going through the various iterations for the monitor. I just don't know! ](*,) Hopefully I can get this thing working properly soon, I'm driving the wife nuts workin' on it. Thanks for the replies, fellas.[/QUOTE]
under the Device section in the /etc/X11/xorg.conf file change the current driver to "vesa" like in the example:
```
Section "Device"
	Identifier	"NVIDIA Corporation NV40? [Unknown nVidia Card]"
	Driver		[COLOR="Blue"]"vesa"[/COLOR]
	BusID		"PCI:1:0:0"
EndSection
```
save the file then restart the xserver by entering ```
sudo /etc/init.d/gdm restart
``` in a terminal or you can just reboot.

---

