---
title: "Modifying xorg.conf"
date: 2010-02-18
forum: General Help
---

### Post by joe.cavers on 2010-02-18
Hi,

I recently did a fresh install of Ubuntu 9.04 and followed these instructions ([http://ubuntuforums.org/showthread.php?t=25151](http://ubuntuforums.org/showthread.php?t=25151)) to enable my Graphire 4 tablet's touch sensitivity. This worked fine last time and there were no problems.

This time however, upon booting up I am greeted with an error saying:

[EE] Problem parsing the config file
[EE] Error parsing the config file

Or something along those lines.
It didn't do this last time I changed xorg.conf, what's going on this time? It works fine if I remove the added txt from the tablet installation instructions.

Cheers
Joe

---

### Post by Favux on 2010-02-18
Hi joe.cavers,

Welcome to Ubuntu forums!

Maybe you were using 8.04 not 9.04 last time?  With Jaunty (9.04) the xorg.conf has been deprecated and linuxwacom is now configured through a .fdi (device information file).  See [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") on the Wacom tablet thread.

Hope this helps.

---

### Post by falconindy on 2010-02-18
There's a syntax error in the xorg config. Post the file and maybe someone can spot the flaw.

---

### Post by joe.cavers on 2010-02-18
Hey,

Was definitely 9.04 last time, it's the only Ubuntu I've ever had.

Here's the xorg.conf file, I'm about to have a look at that link on how to get tablets working.

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

#TABLET CODE BELOW HERE, ORIGINAL FILE ABOVE

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  #USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  #USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"LY
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"
  Option        "USB"           "on"                  #USB ONLYY
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    #For non-LCD tablets only
        InputDevice    "pad"   #For Intuos3/Cintiq 21UX/Graphire4 tablets. It should NOT send core event
EndSection
```


Any thoughts?

Cheers
Joe

Edit: Also, I have followed the instructions for tablet setup in Jaunty in that link. I'm as far as the first reboot, but when I type xinput --list, it only displays the following:
```
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"LITEON Technology USB Multimedia Keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"LITEON Technology USB Multimedia Keyboard"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=4	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Logitech USB Optical Mouse"	id=5	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Wacom Graphire4 4x5"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 10208
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 7424
		Resolution is 10000

```

And "xsetwacom list" returns nothing.
Should I start a separate thread for this?

Cheers
J

---

### Post by falconindy on 2010-02-18
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
[B]	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
[/B]        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    #For non-LCD tablets only
        InputDevice    "pad"   #For Intuos3/Cintiq 21UX/Graphire4 tablets. It should NOT send core event
EndSection
```
Neither of these entries exist. Get rid of them. HAL will find and add your mouse and keyboard for you.

There's probably errors eluding to this in /var/log/Xorg.0.log.

---

### Post by joe.cavers on 2010-02-18
Here's /var/log/Xorg.0.log.

```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux linux-desktop 2.6.28-18-generic #59-Ubuntu SMP Thu Jan 28 01:40:19 UTC 2010 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 18 20:09:26 2010
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 55 of section InputDevice in file /etc/X11/xorg.conf
	"LY" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log
```

Any help at all? I'm completely lost.
J

---

### Post by falconindy on 2010-02-18
Sure it helps. I'm surprised it doesn't choke on the other entries though.

> ```
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 55 of section InputDevice in file /etc/X11/xorg.conf
	"LY" is not a valid keyword in this section.
```
```
Section "InputDevice"
  Driver        "wacom"
  **Identifier    "cursor"LY**
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"
  Option        "USB"           "on"                  #USB ONLYY
EndSection
```

---

### Post by Favux on 2010-02-18
Hi joe.cavers,

OK, xinput is seeing your tablet:
```
"Wacom Graphire4 4x5"	id=6	[XExtensionPointer]

```
But another driver has it, either a mouse or touchpad, which is what [XExtensionPointer] means.  If the linuxwacom drivers had it it would say [XExtensionKeyboard].

Check in Synaptic Package Manager that both linuxwacom packages are installed:  xserver-xorg-input-wacom (it should be) & wacom-tools.

While theoretically you can use a .fdi and the xorg.conf (or another .fdi for that matter) for a device, in practice we've found that doesn't work so well, at least with Wacom.

If you want to use the xorg.conf and not a .fdi remove the .fdi.  Just realize the .fdi gives you usb hotplugging which the xorg.conf doesn't.

You have a usb Wacom Graphire4.  What devices does it have?  Stylus, eraser, cursor (Wacom tablet mouse), pad (buttons on tablet)?

Right now the only thing falconindy & you haven't straightened out is the pad.  It's in "ServerLayout" but does not have a Section.  If you don't have a pad either remove or comment it out in "ServerLayout.

---

### Post by joe.cavers on 2010-02-19
Hey, 

Thanks for all the help so far.

Ok, despite using apt-get in terminal to get both of those, according to Synaptic Package Manager NEITHER of those packages were installed (very odd) so I went ahead and installed them.

I have all the tablet code back in xorg.conf, but still no results.

Do I need to change this:
```
"Wacom Graphire4 4x5"	id=6	[XExtensionPointer]
```

My Graphire4 has Eraser, Stylus and Pad but no cursor (mouse).

Cheers again for the help guys.
Joe

---

### Post by Favux on 2010-02-19
Hi joe.cavers,

> Do I need to change this:

"Wacom Graphire4 4x5"	id=6	[XExtensionPointer]
Yes because that means, now that you've installed the wacom driver and wacom-tools, that you have a wacom.fdi.  That is the name the .fdi is calling your tablet's stylus.  If you want to keep using a .fdi, probably the easiest way to get wacomcpl working is to use a modified .fdi.  For one and explanations and instructions see [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") on the "Wacom tablets in Ubuntu guide/howto" thread.  And of course you'd remove the wacom entries from xorg.conf.

If you want to use the xorg.conf you'll need to remove it or comment the contents out.  It is at:
```
/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi
```
in Jaunty.  And of course you can edit it with:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi
```

I've attached an xorg.conf that should work for your Graphire4 in Jaunty.  Notice I consolidated the video lines in "ServerLayout".  I left the old ones in, but commented out, if that doesn't work.  I think your stylus has two buttons so I added them in also.

Good luck!

---

### Post by joe.cavers on 2010-02-19
Hey Favux,

I set my .fdi back to how it was and put your modified xorg.conf in place.

The tablet now maps to the screen properly (i.e. place the stylus at the far right and the mouse jumps there) but it still doesn't detect different levels of pressure (i.e. in GIMP, regardless of how hard I press, a solid line appears).

The addition of the second and third buttons works perfectly though, thanks!

Thanks again, feels like we're almost there!
Joe

---

### Post by Favux on 2010-02-19
Good!  Progress.

To get pressure in Gimp (and other programs that handle it like Inkscape) you usually have to configure the extended input devices.

See near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom") for instructions.  Hope that does it!

---

### Post by joe.cavers on 2010-02-19
Ah of course sorry, I was forgetting the easy bit! I also meant to say in there previous post that there were no errors on startup anymore either, definitely a good thing!

Thank you so much for all the help! Definitely another positive Ubuntu experience to add to the list there :)

Joe

---

### Post by Favux on 2010-02-19
Hi Joe,

Your welcome.  Glad it's set up!  :)

---

