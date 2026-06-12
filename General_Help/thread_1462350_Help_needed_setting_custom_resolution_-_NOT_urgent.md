---
title: "Help needed setting custom resolution - NOT urgent"
date: 2010-04-25
forum: General Help
---

### Post by kansasnoob on 2010-04-25
**Note to the moderators:** Please don't move this to Lucid testing. While I currently am messing with a Lucid X11 this should also apply to Karmic and possibly even Jaunty. Besides, the Lucid section will go archive very, very soon :)

First of all, as the title says, this is not at all urgent, but I'm visually impaired and recently bought some new hardware. Some patience may be required.

Specific to this the GPU info;

> Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

Previously I'd used VIA graphics w/openchrome drivers and two 16:10 ratio resolutions were available, 1680x1050@61Hz and 1440x900@60Hz. Also Debian Lenny still provides 1440x900 with this Intel GPU, so I know that the "best" resolution for me is 1440x900@60Hz.

Sadly in both Karmic and Lucid (actually even Hardy) only 1680x1050 is available which requires me to jack the fonts so high that certain web pages are distorted. So as time allows I've been studying :)

First the HannsG (22" Wide Screen) manual shows this info:

> Resolution 1440×900 @60Hz WXGA +
Horizontal Frequency (KHz) 55.469
Vertical Frequency (Hz) 59.901

I've also gotten as far as figuring out how to generate an xorg.conf and moved it into place with no ill effects. Here's a copy:

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
	Load  "dbe"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
	Load  "record"
	Load  "glx"
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
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82945G/GZ Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
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

```

So it's definitely a big plus that generating that and moving it into place had no ill effects :D

I also used the "cvt" command and came up with this:

```
lance@lance-desktop:~$ cvt 1440 900
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
```

The thing is I'm almost dumb as a post when it comes to Xorg issues. The heaviest modification I've had to do regarding Xorg was adding "openchrome" to Gutsy and Hardy's xorg.conf to get the old VIA card to work in anything but low graphics :(

And naturally I don't want to fry my 22" Wide Screen. That would be a major bummer. And I'm not absolutely sure if I can depend on that "cvt" output. How reliable is that?

If helpful (I doubt it) this is the Lenny xorg.conf:

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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
EndSection

```

And also the Lenny xrandr:

```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1920 x 1920
VGA connected 1440x900+0+0 (normal left inverted right x axis y axis) 474mm x 297mm
   1680x1050      60.6 +   74.9     60.0  
   1792x1344      60.0  
   1920x1200      60.0  
   1600x1200      75.0     75.0     70.0     65.0     60.0     59.9  
   1600x1024      60.0  
   1400x1050      74.9     74.8     70.0     60.0     60.0  
   1280x1024      75.0     59.9     60.0  
   1440x900       60.2*
   1280x960       60.0     59.9  
   1280x800       60.0  
   1152x864       75.0     74.8  
   1280x768       60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
```

Anyway I'm currently looking here:

[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf)

But things look so different in that Lucid xorg.conf that I generated I'm just a bit lost. I haven't tried but I'd expect generating an xorg.conf in Karmic would be about the same.

I should also say that I do iso testing so don't be surprised if I disappear for a few days :)

I'm just in hopes that someone with xorg customizing experience would provide some examples of editing, that is just what to put where, or what steps I should take next.

Any help will be immensely appreciated.

---

### Post by klemes on 2010-04-25
I think the simplest solution for your problem would be to have X make a new xorg.conf from scratch by typing in the terminal  logged in as  a user( a virtual terminal (tty) not a console program inside X eg gnome-terminal)

```
sudo X -configure
```This will generate a new xorg.conf located in your home directory named xorg.conf.new
You can first test the new xorg by running:

```
Sudo X -config ~/xorg.conf.new
```If it works and it will work then proceed to edit the xorg.conf.new manually.
Search in the Monitor section all the Modeline lines then search if your desired 
monitor resolution is there.If it is then proceed to edit the Screen section as follows:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor       "Monitor0"
    DefaultDepth    24
   SubSection     "Display"
       Depth       24
       Modes      "1440x900@60" 
   EndSubSection
EndSection
```You may or may not have to modify accordingly the words Screen0 Videocard0 and Monitor to those used by your specific generated xorg.conf.new.
Retest the new xorg by the previous command and if you should have your desired resolution as default

If however for some reason you do not have your specified resolution listed to one of the modelines you simply add one having as contents the output of the cvt command.

Here's also a link for a very straightforward guide about adding custom modes using cvt and xrandr:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

Good Luck!!!!:guitar::guitar::guitar:

EDIT: forgot to tell you that once you are done editing and testing and you are satisfied with the results you must copy your ~/xorg.conf.new to /etc/X11/xorg.conf overwriting the previous file.(you can backup first if you want).

---

### Post by klemes on 2010-04-25
```
#cvt 1440 900
``````
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

```The above it's the output of the cvt command for the resolution you have asked.....


Use the above modeline and you should be alright......:)

---

### Post by kansasnoob on 2010-04-25
I did forget to mention that I've already tried the "temp" changes and that was fine, where I stumble is exactly how to edit the new xorg.conf.

This is what I have:

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
	Load  "dbe"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
	Load  "record"
	Load  "glx"
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
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82945G/GZ Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
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
```

I've run that for a while to be sure there were no regressions or problems of any kind and it all seems good.

Where my confusion sets in is the actual editing. Should I trust the output of "cvt"?

If so exactly how should I edit? Look at what the Wiki says:

[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf)

Then look at the applicable sections of my new xorg.conf:

```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82945G/GZ Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
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

```

I dislike trial and error!

---

### Post by klemes on 2010-04-26
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        Modeline     "1440x900@60" 106.50 1440 1528 1672 1904 900 903 909 934 -hsync +vsync
End Section

---

### Post by klemes on 2010-04-26
Section "Screen"
    Identifier    "Screen0"
    Device        "Card0"
    Monitor       "Monitor0"
    DefaultDepth    24
   SubSection     "Display"
       Depth       24
       Modes      "1440x900@60" 
   EndSubSection
EndSection

:popcorn:

Sorry for the two separate posts I had no way of merging those...
Just edit your above two xorg sections accordingly.That's all you will have to do.:guitar:

---

### Post by kansasnoob on 2010-04-26
Many thanks. I'll give that a whirl sometime in the next couple of days.

---

### Post by kansasnoob on 2010-04-28
Just wanted to stop in and thank klemes again. While the changes to xorg.conf did work, I found it much better to edit '/etc/gdm/Init/Default' as described in the link you provided.

It's also not a "hack" because it's mentioned briefly in official Ubuntu docs:

[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts)

Many. many thanks again.

---

### Post by kansasnoob on 2010-04-30
I actually did run into a minor glitch with editing "/etc/gdm/Init/Default". It works fine unless you choose to use auto-login, then it doesn't work so I found that editing "/etc/gdm/PreSession/Default" was preferable:

[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

---

### Post by kansasnoob on 2010-08-21
I ran into some minor glitches recently so I thought I'd follow up on this in case it shows up in someones search :)

First let me recap. If I'm using the standard Ubuntu/Gnome desktop either of the following solutions is fine:

[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

There are minor caveats with both however. The first link works fine with or without auto-login but it does not change the GDM screen resolution. The latter link appears to change both the GDM resolution and the screen resolution, but it doesn't work if you choose to "auto-login". You can however do both and they work just fine together:D

But recently I've been playing with other desktops, particularly LXDE derivatives like Lubuntu and Peppermint, not because I'm giving up on Gnome or Ubuntu, but because I'm looking for lightweight alternatives for older machines and it's much easier to play on my own familiar machine than to play on some unfamiliar hardware ;)

Anyway this required the dreaded creation and modification of an xorg.conf since "gdm" is not used by default without Gnome. Using the suggested edits did work, but I was experiencing occasional X-freezes, flickering, screen resizing during reboot, etc. so I continued playing. Here's what ended up working (I didn't need to remove anything, so all additions are in red):

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
	Load  "dbe"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
	Load  "record"
	Load  "glx"
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
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        [B][COLOR="Red"]Modeline     "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
        Option       "PreferredMode" "1440x900_60.00"[/COLOR][/B]
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82945G/GZ Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
                **[COLOR="Red"]Modes    "1440x900@60"[/COLOR]**
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
                **[COLOR="Red"]Modes    "1440x900@60"[/COLOR]**
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
                **[COLOR="Red"]Modes    "1440x900@60"[/COLOR]**
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
                **[COLOR="Red"]Modes    "1440x900@60"[/COLOR]**
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
                **[COLOR="Red"]Modes    "1440x900@60"[/COLOR]**
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
                **[COLOR="Red"]Modes    "1440x900@60"[/COLOR]**
	EndSubSection
EndSection

```

Why it didn't work with only a default "Depth 24" I don't know but I guess either the Hanns-G monitor or the Intel 82945G/GZ wasn't happy.

Hopefully this might help someone else in the future. Naturally you'll have to use "xrandr" and "cvt" to determine the proper parameters. etc :D

---

