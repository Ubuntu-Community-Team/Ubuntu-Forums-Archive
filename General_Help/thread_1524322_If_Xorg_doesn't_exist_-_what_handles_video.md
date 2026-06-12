---
title: "If Xorg doesn't exist - what handles video?"
date: 2010-07-05
forum: General Help
---

### Post by Roasted on 2010-07-05
My laptop has an Intel video card. Does Intel have open source drivers that are included in the kernel? I'm kind of curious because I do not have a xorg file, and I did not install any drivers as I had to on my nvidia desktop, yet all of my maximum resolutions come down accordingly.

I'm just curious on what exactly controls the video settings if xorg isn't in the picture.

Also - what relevance does the Fn keys have that probe for a 2nd monitor to Ubuntu? For example, I do not have a 2nd monitor attached, but if I hit Fn F8 over and over, sometimes it changes my resolution. Why is this? Why would that revert my resolution?

---

### Post by efflandt on 2010-07-05
There are standard X modules that try to figure out everything automatically without any xorg.conf.  You can see mostly how it determines what in /var/log/Xorg.0.log.  So xorg.conf is really only necessary if you need to set something specific that is not automatic, particularly for optional proprietary video drivers.

One thing that does not seem to be that automatic is video modes for VGA.  Digital connections like DVI or HDMI usually more automatically communicate their capabilities to the video source to automatically use the native resolution of a display.  But VGA often provides just standard video modes, so you may need to do some configuration to use a resolution not on the default list.

Since I am using a DVI to HDMI connected HDTV as a monitor on my desktop, that is automatic.  So the only thing I need to configure is for connecting VGA from my laptop.  When I boot with an external display connected it tends to use a common resolution for both displays which ends up at 1024x768.  So I use a bash script with xrandr commands and a launcher that I can simply double click to shut off my laptop display and switch the external display to the desired resolution.  I actually have one script for 1080p and another for a different 720p HDTV.

Info for setting X resolutions: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Roasted on 2010-07-05
Hm, I see. I'm just trying to understand why I can sit there and reboot my laptop 15 times in a row, and maybe 2 or 3 of those times it comes up with a borked screen. Sometimes the resolution drops back to 1024x768 instead of the native 1280x800. Other times the login screen is off to the right where a 2nd monitor WOULD be, but is not. There's nothing connected to the laptop, yet sometimes it thinks there's a 2nd monitor connected. I'm just not sure what I could do to make this more concrete to open @ 1280x800 each. and. every. single. time.

:(

---

### Post by Roasted on 2010-07-07
Up. Sick of booting up and having the wrong resolution. It'd be fine if I could just Fn + F8 and slap it back to proper resolution, but when I do it knocks my icons in my top panel all out of wack, even if they're locked.

Any fixes?

---

### Post by Grenage on 2010-07-07
It's probably a bad cable, or dodgy connection - but anything that interferes with EDID can cause incorrect resolutions.  The only 'fix' I can suggest is an xorg.conf file; they're pretty easy to knock up.  Here is a [guide]("http://www.grenage.com/xorg.html") I wrote a while ago, but there are many others on the net to choose from.

---

### Post by Roasted on 2010-07-07
> **Grenage said:**
> It's probably a bad cable, or dodgy connection - but anything that interferes with EDID can cause incorrect resolutions.  The only 'fix' I can suggest is an xorg.conf file; they're pretty easy to knock up.  Here is a [guide]("http://www.grenage.com/xorg.html") I wrote a while ago, but there are many others on the net to choose from.

It's not a bad cable. It's a laptop. It worked great with Ubuntu 9.10, and only started with Ubuntu 10.04.

I did get a xorg.conf file. I ran a command to auto generate one. The problem still persisted, unless I didn't set up the xorg file right. It was just one command - does that sound normal?

---

### Post by Grenage on 2010-07-07
That is pretty normal, but you can 'hard-code' the resolutions you desire.  That _won't_ be misinterpreted by the system.

---

### Post by Roasted on 2010-07-07
> **Grenage said:**
> That is pretty normal, but you can 'hard-code' the resolutions you desire.  That _won't_ be misinterpreted by the system.

Would hard-coding the resolution be taken care of @ the boot screen level + regular system level after I log in?

How would I accomplish this? I know my native rez so I don't need to probe or whatever. Just curious on how I can kung foo ninja change it and call it a day.

---

### Post by Grenage on 2010-07-07
You can do it from the desktop, or a basic terminal.  The guide I linked to has all the syntax and info you should need; if you're still unsure, post back.

---

### Post by Roasted on 2010-07-07
Yeah, I really have no idea. I remember running a series of commands way back which would auto detect my native rez and plug it in to the xorg and I was good to go. How do I do that?

I also found this basic xorg. If I have to manually edit it, I can... where do I add the rez?

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

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
```

---

### Post by The Cog on 2010-07-07
> **Roasted said:**
> Hm, I see. I'm just trying to understand why I can sit there and reboot my laptop 15 times in a row, and maybe 2 or 3 of those times it comes up with a borked screen. Sometimes the resolution drops back to 1024x768 instead of the native 1280x800. Other times the login screen is off to the right where a 2nd monitor WOULD be, but is not. There's nothing connected to the laptop, yet sometimes it thinks there's a 2nd monitor connected. 
Happens to me too. Dall latitude E5500 laptop, intel graphics.
> Up. Sick of booting up and having the wrong resolution. It'd be fine if I could just Fn + F8 and slap it back to proper resolution, but when I do it knocks my icons in my top panel all out of wack, even if they're locked.
I have been doing Ctrl-Alt-F1, Ctrl-Alt-F7 to get it back. It's very irritating when it shuffles the panel icons, I know.
I also noticed that simply starting the Monitors application corrects it (no need to click anything). Also, starting Movie Player can make the screen resolution switch.

I think it's a problem with the intel drivers. 
I'll have a look at the guides later.

---

### Post by Grenage on 2010-07-07
You only need to specify the parts that you need, the system will automatically take care of the rest (as it does with your graphics most of the time).

Far that reason I would suggest not using other people's configs, and just creating your own.  If you know what res you need, you can specify it using a modeline, that is listed on the lower end of the guide.

---

### Post by Roasted on 2010-07-07
Well, I see several instances of "modeline" in the guide, but not sure what commands I have to run...

Getting a little frustrated with this, so I apologize for the blunt question... what command do I need to get xorg to work with the native rez?

---

### Post by Grenage on 2010-07-07
> **Roasted said:**
> Well, I see several instances of "modeline" in the guide, but not sure what commands I have to run...

The command is listed in the example, and above - it's *cvt*

> Getting a little frustrated with this, so I apologize for the blunt question... what command do I need to get xorg to work with the native rez?

I know it can be a pain.  Take below as an example:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "unknown"
	ModelName "unknown"
***Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync***
EndSection

Section "Device"
	Identifier "Device0"
***	Driver "intel"***
	VendorName "Intel 945GM"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x800"
	EndSubSection
EndSection
```

I've highlighted areas of interest.  The driver used will depend entirely on your graphics card (intel/ati/vesa et cetera); you *might* be able to remove that one line, and it will just use whatever driver it has been using.  The modeline is what specifies a resolution and its frequency settings.

Normally you would also have vertical and horizontal frequencies listed, but I don't know what yours are - it may well work without them.

Display section at the bottom is where we have set the default resolution.

---

### Post by Roasted on 2010-07-07
Well, did that. Came up as in low graphics mode. Dropped to terminal and renamed xorg.conf to something else so I could start like normal.

My Xorg: [http://pastebin.org/385375](http://pastebin.org/385375)

On second thought, I booted up and sure enough the login screen gave me the wrong rez. Instead of fumbling with Fn + F8, I just logged in anyway. It auto corrected to my native resolution. Perhaps I should just suck up that the login screen may be borked and deal with it. The only thing that pisses me off about the login screen is there's times I boot up, and it's just gone. Where is it? Sitting on the right, where a monitor "would" be if I had a 2nd display attached. That's what bugs me - but the resolution I suppose isn't a big deal... I really don't feel like spending hours messing with this to fix a small issue.

---

### Post by The Cog on 2010-07-07
Thinking about it, I think the problem is that X sees an imaginary second screen, and auto adjust the resolution for a two-screen setup. I think the card cannot handle two screens at full resolution, so it reduces the resolution until the card can handle both screens.

During the Lucid betas, I noticed the boot screen scrolling messages about a screen has been connected, a screen has been disconnected a few times. So setting the desired mode for one screen isn't going to help.

---

### Post by Roasted on 2010-07-07
> **The Cog said:**
> Thinking about it, I think the problem is that X sees an imaginary second screen, and auto adjust the resolution for a two-screen setup. I think the card cannot handle two screens at full resolution, so it reduces the resolution until the card can handle both screens.

During the Lucid betas, I noticed the boot screen scrolling messages about a screen has been connected, a screen has been disconnected a few times. So setting the desired mode for one screen isn't going to help.

Interesting thought. Is there any form of fix I can do on my own? Or is it one of those wait till a patch comes kind of deals?

I HAVE seen filed bugs regarding this issue, so it's not like I'm praying it gets fixed on accident...

---

### Post by Grenage on 2010-07-07
> **Roasted said:**
> Well, did that. Came up as in low graphics mode. Dropped to terminal and renamed xorg.conf to something else so I could start like normal.

My Xorg: [http://pastebin.org/385375](http://pastebin.org/385375)

On second thought, I booted up and sure enough the login screen gave me the wrong rez. Instead of fumbling with Fn + F8, I just logged in anyway. It auto corrected to my native resolution. Perhaps I should just suck up that the login screen may be borked and deal with it. The only thing that pisses me off about the login screen is there's times I boot up, and it's just gone. Where is it? Sitting on the right, where a monitor "would" be if I had a 2nd display attached. That's what bugs me - but the resolution I suppose isn't a big deal... I really don't feel like spending hours messing with this to fix a small issue.

Hi again.

The example I posted is the sort of thing I would recommend in entirety - you won't need any of that other stuff.  You're also lacking anything that specifies the default resolution, or any resolution to use.

Try using the example I gave you, but remove the *driver* line unless you happen to be using an intel graphics chipset.

---

