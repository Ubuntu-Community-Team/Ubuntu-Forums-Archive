---
title: "Genius EasyPen i405 Tablet in Jolicloud."
date: 2011-06-13
forum: General Help
---

### Post by FabShade on 2011-06-13
Hi I'm new in the forum, and I need help, some days ago was my Birthday, so my mother bought me a Genius EasyPen i405 Tablet, but it only has the drivers for Mac and Windows, and I use Jolicloud (It's almost the same as Ubuntu) and can't use it.

Someone can help me? I'm trying to study graphic design, so I really need this

If you can make it the most explained possible, I am a bit new in Linux. Also I already installed WizardPen and the Tablet works almost fine, the problem is that when I put the pen on the tablet the coursor goes to the top of the screen, but I can't move it.

Thank you all.

PS: I use Jolicloud 1.2, it's like Ubuntu 11.04 (I think)
PS2: Sorry if my grammar is poor, my language is Spanish.

---

### Post by Favux on 2011-06-14
Hi FabShade,

Welcome to Ubuntu forums!

When the cursor goes to the top left corner it indicates the tablet is not on a X driver.  Or at least one that works for it.  So the X server isn't getting coordinate values.  Top left corner is 0,0.

Let's make sure the WizardPen driver is the correct one for the Genius EasyPen i405 Tablet.

Post the output of the line with the tablet in it, after entering in a terminal:
```
lsusb
```
Also post the output of:
```
xinput list
```

---

### Post by FabShade on 2011-06-14
Thanks for answering Favux. This is what appear on the terminal:

> $ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 10f1:1a08  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                 	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Webcam-101                              	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=13	[slave  keyboard (3)]


I'm not sure about what does that means so I can't make any comment about that.

---

### Post by Favux on 2011-06-14
It tells us that it is a UC-LOGIC tablet which does use the wizardpen driver.  So the keyword UC-LOGIC should work in the 70-wizardpen.conf in xorg.conf.d for matching the tablet to place it on the WizardPen X driver.

Let's see what driver it is currently on.  Run this command in a terminal and post the results.
```
xinput list-props "UC-LOGIC Tablet WP5540U"
```

How did you install the WizardPen driver?  What did you do?

---

### Post by FabShade on 2011-06-14
It appears:

> $ xinput list-props "UC-LOGIC Tablet WP5540U"
Device 'UC-LOGIC Tablet WP5540U':
	Device Enabled (132):	1
	Device Accel Profile (261):	0
	Device Accel Constant Deceleration (262):	1.000000
	Device Accel Adaptive Deceleration (264):	1.000000
	Device Accel Velocity Scaling (265):	10.000000
	Evdev Reopen Attempts (250):	10
	Evdev Axis Inversion (266):	0, 0
	Evdev Axis Calibration (267):	<no items>
	Evdev Axes Swap (268):	0
	Axis Labels (269):	"Abs X" (256), "Abs Y" (257), "Abs Z" (258), "Abs Rotary X" (259), "Abs Pressure" (260)
	Button Labels (270):	"Button Left" (133), "Button Middle" (134), "Button Right" (135), "Button Wheel Up" (136), "Button Wheel Down" (137), "Button Horiz Wheel Left" (138), "Button Horiz Wheel Right" (139), "Button Side" (253), "Button Extra" (254), "Button Forward" (255), "Button Unknown" (251), "Button Unknown" (251), "Button Unknown" (251), "Button Unknown" (251)
	Evdev Middle Button Emulation (271):	2
	Evdev Middle Button Timeout (272):	50
	Evdev Wheel Emulation (273):	0
	Evdev Wheel Emulation Axes (274):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (275):	10
	Evdev Wheel Emulation Timeout (276):	200
	Evdev Wheel Emulation Button (277):	4
	Evdev Drag Lock Buttons (278):	0


To install it I followed this tutorial: [http://ubuntuforums.org/showthread.php?t=1337260](http://ubuntuforums.org/showthread.php?t=1337260)

---

### Post by Favux on 2011-06-15
Alright, the tablet is on the evdev X driver which is why it isn't working.

So either the driver isn't working correctly or you do not have a wizardpen.conf installed to place the tablet on it.  Were there any problems with the configure and make?  Errors thrown up?

For the wizardpen.conf look in /usr/share/X11/xorg.conf.d for it.  It will probably be preceded by the number 70.  If it is there post the output.

---

### Post by FabShade on 2011-06-15
> **Favux said:**
> Alright, the tablet is on the evdev X driver which is why it isn't working.

So either the driver isn't working correctly or you do not have a wizardpen.conf installed to place the tablet on it.  Were there any problems with the configure and make?  Errors thrown up?

For the wizardpen.conf look in /usr/share/X11/xorg.conf.d for it.  It will probably be preceded by the number 70.  If it is there post the output.

The folder doesn't appears in /usr/share/X11, but it appears in usr/lib/X11/, but doesn't have any archive or folder that preceds by the number 70, the only archives that appears are: "05-evdev.conf", "10-synaptics.conf" and "10-vmmouse.conf".

---

### Post by Favux on 2011-06-15
Alright, use of */usr/lib/X11/xorg.conf.d* indicates Lucid's hybrid X server 1.7.  To check run in a terminal:
```
Xorg -version
```
and post the output.  That is a non-standard location so even if packages try to install the .conf they often try the standard location and fail because it isn't there.

So assuming the WizardPen driver works we need a wizardpen.conf for you.  There should be one in the uncompressed source code folder if you compiled it.  Otherwise I've posted a few versions and the default version with DoctorMO's PPA is posted to:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)

---

### Post by FabShade on 2011-06-15
> **Favux said:**
> Alright, use of */usr/lib/X11/xorg.conf.d* indicates Lucid's hybrid X server 1.7.  To check run in a terminal:
```
Xorg -version
```
and post the output.  That is a non-standard location so even if packages try to install the .conf they often try the standard location and fail because it isn't there.

So assuming the WizardPen driver works we need a wizardpen.conf for you.  There should be one in the uncompressed source code folder if you compiled it.  Otherwise I've posted a few versions and the default version with DoctorMO's PPA is posted to:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)

In the Terminal appears:

```
X.Org X Server 1.7.6.901 (1.7.7 RC 1)
Release Date: 2010-04-12
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.35-23-generic-pae i686 Ubuntu
Current Operating System: Linux PixelBot 2.6.35.10-1-jolicloud-atom #64 SMP Fri Mar 4 04:39:01 MST 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35.10-1-jolicloud-atom root=UUID=deb2e8e7-e68a-4504-bceb-a1dfe1be8489 ro quiet splash
Build Date: 09 February 2011  12:14:22PM
xorg-server 2:1.7.6.901-0jolicloud2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.

```

And when I try to put the ppa appears this error message:

```
Can't found the method /usr/lib/apt/methods/ppa.Can't found the method /usr/lib/apt/methods/ppa.
```

---

### Post by Favux on 2011-06-15
OK, you do have the Debian/Ubuntu hybrid X server 1.7.  It has some of an early version of 1.8 backported into it so they could get rid of HAL as soon as possible.

Doesn't look like you can use an Ubuntu PPA on Jolicloud.  That's too bad.  DoctoMO's version of the WizardPen driver does work.

Let's try putting in a wizardpen.conf.  Enter in a terminal:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/70-wizardpen.conf
```
Then copy and paste the following entire contents into the empty file:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
Save, Close, and reboot.

---

### Post by FabShade on 2011-06-15
Now it doesn't moves the cursor, but the LED of the Tablet is on.

---

### Post by Favux on 2011-06-15
Repeat the *xinput list-props* command and see where we are.

---

### Post by FabShade on 2011-06-15
It appears:

```
$ xinput list-props
Usage: xinput list-props <device> [<device> ...]

```

Also I put the name of the tablet:

```
$ xinput list-props UC-LOGIC-Tablet-WP5540U
unable to find device UC-LOGIC-Tablet-WP5540U

```

It looks like now don't reconogize the tablet.

---

### Post by Favux on 2011-06-15
You have to use the quotes:
```
xinput list-props "UC-LOGIC Tablet WP5540U"
```

---

### Post by FabShade on 2011-06-15
It says the same:

```
$ xinput list-props "UC-LOGIC Tablet WP5540U"
unable to find device UC-LOGIC Tablet WP5540U

```

---

### Post by Favux on 2011-06-15
What does *xinput list* show now?

---

### Post by FabShade on 2011-06-15
```
$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Webcam-101                              	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=13	[slave  keyboard (3)]

```

---

### Post by Favux on 2011-06-15
My guess is we now have the tablet placed on the wizarpen driver but the driver isn't working for whatever reason.

Let's try updating your driver.  Can you use a Debian package?  Does Jolicloud have a Debian Package Installer?  If so grab the deb or source code if not from:  [https://launchpad.net/wizardpen](https://launchpad.net/wizardpen)  I'm assuming the latest still builds on Lucid.  And drpjkurian has updated instructions on the wiki it links to:  [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

---

### Post by FabShade on 2011-06-15
> **Favux said:**
> My guess is we now have the tablet placed on the wizarpen driver but the driver isn't working for whatever reason.

Let's try updating your driver.  Can you use a Debian package?  Does Jolicloud have a Debian Package Installer?  If so grab the deb or source code if not from:  [https://launchpad.net/wizardpen](https://launchpad.net/wizardpen)  I'm assuming the latest still builds on Lucid.  And drpjkurian has updated instructions on the wiki it links to:  [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)


Yes I can install Debian Packages, I can't find the package in the site, so I'm installing it in a terminal.

---

### Post by Favux on 2011-06-15
Oops, you're right.  Just source code.  Back to DocorMO's site, he has deb.s in there.  Just pick the one for your system, i.e. 64-bit(amd64) or 32-bit(i386):  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages](https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages)  Click on the triangle by the Lucid package and it will have the deb.s in there.

---

### Post by FabShade on 2011-06-15
It appear another error message when I try to install the .deb (I already installed another .deb's so I know it works) :confused:

```
(Reading database... 00% 103942 files and directories installed actually)

Unpacking xserver-xorg-input-wizardpen (of .../xserver-xorg-input-wizardpen_0.7.3-1ubuntu1_i368 (1).deb) ...
dpkg: error procesing /home/user/Documents/WizardPEn/xserver-xorg-input-wizardpen_0.7.3-1ubuntu1_i368 (1).deb (--install):
 trying overwrite `/usr/lib/xorg/modules/input/wizardpen_drv.la', that also is in the package wizardpen 0:0.7.0-apha2
Precesing shooters for hal...
Regenerating hal fdi cache ...
It foun errors processing: 
 /home/user/Documents/WizardPen/xserver-xorg-input-wizardpen_0.7.3-1ubuntu1_i368 (1).deb

```

I made the traduction of Spanish to English, sorry for the spelling mistakes.

---

### Post by Favux on 2011-06-15
Shoot.  There might be a Ubuntu specific problem with the package.  Was the other deb from Ubuntu or just a generic Debian?

Looks like you'll have to compile from the source code then.

A little late, but there's no Jolicloud package available for wizardpen I assume?

---

### Post by FabShade on 2011-06-15
> **Favux said:**
> Shoot.  There might be a Ubuntu specific problem with the package.  Was the other deb from Ubuntu or just a generic Debian?

Looks like you'll have to compile from the source code then.

A little late, but there's no Jolicloud package available for wizardpen I assume?

No, it isn't, I think I may change my OS to an official Ubuntu version.

---

