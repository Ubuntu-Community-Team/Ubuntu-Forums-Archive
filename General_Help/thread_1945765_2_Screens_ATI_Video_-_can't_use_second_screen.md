---
title: "2 Screens ATI Video - can't use second screen"
date: 2012-03-23
forum: General Help
---

### Post by erinspice on 2012-03-23
I'm having the same problem described [here]("http://ubuntuforums.org/showthread.php?t=1438359") (post closed) which I will describe again.

I have Radeon HD 34xx with 2 identical monitors set up in landscape, side-by-side, on Natty/Unity with fglrx 2:8.840-0ubuntu4. However, I cannot put stuff on the right screen. It's displaying the desktop in the correct resolution, but I cannot move windows from my left screen to my right screen, and since there are no panels on the right screen, I cannot use it at all. When I attempt to drag a window to the right screen, it just disappears off the left screen and never shows up on any screen or workspace.  How can I fix this? I don't know where to start troubleshooting.

---

### Post by QIII on 2012-03-23
I'm not at my machine right now so I can't walk through it to describe it, but...

In the catalyst control center, take a look at your monitor settings.  There should be a set up tab with a representation of your monitors with a colorful fish on it.

If you want to have your workspace span both monitors, choose the selection showing a single fish with one half on one screen and the back half on the other.

Save the setting and reboot.

---

### Post by erinspice on 2012-03-23
Thanks for the reply. I didn't know about CCC. I have been editing the configs manually this whole time! 

That doesn't work (yet) because CCC isn't saving my settings. :( I'll turn on single desktop and then reboot and it'll still be off.

---

### Post by QIII on 2012-03-23
Are you getting any feedback from CCC, or does it appear to accept your changes?

---

### Post by erinspice on 2012-03-23
No errors. I click "Apply", click "Yes" to confirm a time or two, and then click "OK" to close the window, but there are no changes to xorg.conf and no changes to my display setup on reboot. I tried deleting xorg.conf before rebooting, and I just got a default xorg.conf with the second display cloning the first.

---

### Post by QIII on 2012-03-23
Could you post the contents of your xorg.conf?

Please put it between code tags by first clicking the pound sign in the buttons above.

---

### Post by erinspice on 2012-03-23
```
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option		"SWCursor" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen		1
EndSection

```

---

### Post by QIII on 2012-03-23
There should be another section in there that gives the "virtual" screen as (width1+width2)xheight -- say 3840x1080 if you have two 1920x1080 monitors.

Not sure if I'll get a chance to get to it tonight, but I'll post back a copy of my xorg.conf as soon as I can.

---

### Post by imachavel on 2012-03-23
I have never ever used dual display in ubuntu, or any other OS. I once bought a graphics card with dual vga adapter display abilities. And the computer didn't like the drivers, scratch that the card was damaged because the bios loading screen was fuzzy. So I installed an hd card after I sent that one back, never got an hd monitor though, and tried using the onboard vga port as well as the installed hd card in computers expansion slot(agp, pci version.........? don't remember)

lol big mistake the computer will disable onboard always when a video card is in an expansion slot. Ok so now that I have explained that, I can't seem to set up monitor display in the top right gear power button looking icon(I've set to unity interface), well yes I can it just isn't detecting dual display because I don't have it set up. So I can't troubleshoot for you very well. Is one of the hd cards you are using an nvidia card? In the terminal

ctrl+alt+t

please type gksudo nvidia. Thanks

as for your code configuration, can't help you with it because I just don't know. Sorry

---

### Post by erinspice on 2012-03-23
No, I am using 1 dual-head Radeon HD 34xx. No nvidia.

---

### Post by imachavel on 2012-03-23
also I was going to try to compare my xorg.conf to help you out:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
danel@danel-Dimension-4700:~$ 

as you can see, the command was entered, but really I don't know what it did. No error return syntax, but no conf file popping up to try and compare my settings, which obviously won't help you since I don't have dual display set up. I'd ask you to type in

lspci in the terminal, to list installed drivers. But you said drivers were installed for the video card so dual display would work, and only recently did the dual display stop functioning. Sounds like a .conf issue for sure.

---

### Post by imachavel on 2012-03-23
> **erinspice said:**
> No, I am using 1 dual-head Radeon HD 34xx. No nvidia.

oh right, not sure of the radeon display panel will pop up in ubuntu. Really I'm surprised that doesn't need to be installed. In windows I had to install nvidia control panel as well. I wish I knew what the ubuntu equivalent was for dxdiag. Dxdiag helps a ton showing what version of directx you use. But then ubuntu video api I believe is opengl, not directx, so it'd be useless.

---

### Post by erinspice on 2012-03-23
My drivers are installed correctly and working just fine as is evidenced by the fact that the dual monitors work at all and the fact that there is hardware acceleration going on.

---

### Post by QIII on 2012-03-23
The OP clearly stated that he/she is using an ATI HD card and the proprietary driver.

Adjustments should be made through CCC.  However, that is not working for some reason and should be rectified.

In the interim, I would like to get the OP's xorg.conf configured manually so he/she can use both monitors in an extended desktop.

It is somewhat less than helpful when someone jumps in, says they don't know what they are saying and then says something anyway.  We have all given poor advice from time to time.  I certainly have done that with embarrassing frequency.  However, it would be best, knowing we don't know what we are talking about, to simply not chalk up a bean.

---

### Post by erinspice on 2012-03-23
QIII: It's "she". :)

---

### Post by imachavel on 2012-03-23
ok. I was hoping to learn something also. ANyway....... I'm out

---

### Post by QIII on 2012-03-23
OK, erinspice.  Sometimes it is unwise to presume.  ;)

My daughter's middle name is Erin.

---

### Post by QIII on 2012-03-23
Imachavel...

Taking interest and reading is a good thing.  I encourage you to do that.  I do more of that here than typing.

---

### Post by erinspice on 2012-03-23
Another strange symptom: All keyboard presses and possibly some mouse clicks only affect the left screen.

I can right-click on the right screen and choose "Add Launcher". (I was going to add a terminal launcher to see if new processes would pop up on the second screen if the launcher was located there.)  The "Add Launcher" dialog popped up on the second screen, but when I clicked on it, the text box was not highlighted and text entered there showed up in my browser URL bar, which is located on the first screen.

---

### Post by QIII on 2012-03-23
Oh!  You are just bound and determined to make this difficult, arent you?

Mouse click works, dialog pops up.  No keyboard input.  Grrr.

Have you tried the process without your browser running?

---

### Post by erinspice on 2012-03-23
Without the browser running, the keyboard entries just go off into Never Never Land, with mouse clicks still being meaningful on screen 2.

---

### Post by QIII on 2012-03-23
You don't own a shotgun, do you?

OK.  I'll try to get back to this, but I can't guarantee how soon.

(Step away from the shotgun, Miss...)

---

### Post by QIII on 2012-03-25
Still there, erinspice?

Took a bit longer to get back to this than I thought.

This wasn't happening when you were using the open source, default driver that comes with Ubuntu?

I'm going to post my xorg.conf, but remember that his will not likely be exactly what you need.

Notice my "Monitor" sections and the additional info I have there.  Also notice that for the second monitor I have "Position" "1920 0".  This makes sure the upper left corner of the right hand screen matches the upper right hand corner of the left hand screen.

Notice the "Screen" sections. The second on particularly.  Notice the word "Virtual"  That's for 1920x1080 resolution.

All through the xorg.conf, there will be differences based on resolution, refresh rates, etc.

Don't take this as gospel, because it is surely going to need some changes due to your particular case.  And make a copy of your current xorg.conf before you do anything, of course.

I still haven't found anything on the weird I/O issues.  Still poking around on that one.

```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "0-DFP3"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP4"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "61"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP3" "0-DFP3"
    Option        "Monitor-DFP4" "0-DFP4"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3840 1920
        Depth     24
    EndSubSection
EndSection
```

---

### Post by erinspice on 2012-03-26
OK, I think we are almost there. I've incorporated most of your changes into my config, and now I'm getting #2 cloning #1. Can you spot an error or omission here?

```
Section "Module"
	Load	"glx"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    #Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    #Option        "TargetRefresh" "61"
    Option        "Position" "1680 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option		"SWCursor" "on"
	Option		"Monitor-DFP3" "aticonfig-Monitor[0]-0"
	Option		"Monitor-DFP4" "aticonfig-Monitor[0]-1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	#Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Virtual		3360 1680
		Depth     24
	EndSubSection
EndSection

```

---

### Post by erinspice on 2012-03-26
The names "Monitor-DFP3" and "Monitor-DFP4" are definitely wrong.  I have mentions of DFP1, DFP2, CRT1, and CRT2 in my Xorg.0.log.  The closest I've gotten so far is when I tried DFP1 and CRT2, the windows were cloned between the two monitors, but my mouse was not, and the video on monitor #2 was distorted.


EDIT: I got it working. I had moved the Virtual directive, so renaming the monitors should have worked by itself.  This also solved my input problems. Thanks, QIII!

final:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    #Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    #Option        "TargetRefresh" "61"
    Option        "Position" "1680 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	#Option		"SWCursor" "on"
	Option		"Monitor-DFP1" "aticonfig-Monitor[0]-0"
	Option		"Monitor-CRT2" "aticonfig-Monitor[0]-1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	#Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth	24
	SubSection "Display"
		Virtual		3360 1680
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

