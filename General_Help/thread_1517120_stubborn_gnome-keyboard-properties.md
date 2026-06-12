---
title: "stubborn gnome-keyboard-properties"
date: 2010-06-24
forum: General Help
---

### Post by jesuisbenjamin on 2010-06-24
Hello there,


I have an issue with the keyboard layout settings.

During installation of 10.04 i installed USA international (dead keys). Then after the installation, realising i chose the wrong one, i added USA international (ALTGR dead keys) and removed the former and applied system-wide.

Yet when rebooting, the former keyboard shows up together with the latter.

I looked into gnome-keyboard-properties, the man page says not much but states: > The online documentation available through the program's Help menu. But when i open gnome-keyboard-properties and press help, the window simply shuts down.

It's not handy at all.

I want to remove the former completely of my settings. Is there a file i can edit to do so?

(PS: i find there are too many gnome-related bugs in 10.04, it's disappointing :( )

Thanks! :)

---

### Post by VH-BIL on 2010-06-24
System > Preferences > Keyboard
Use the "Layouts" tab.

---

### Post by jesuisbenjamin on 2010-06-24
Thanks man,

but as i said in my previous post: it's what i did, but on reboot the former keyboard layout returns.

Also i have run gconf-edit and i checked the key /desktop/gnome/peripherals/keyboard/kbd/layouts where the layouts value has only us altgr-intl, the other value which returns at boot is not visible. This makes me think some other app is adding the former layout at startup. Is this possible? It sounds like a silly system. 

(i reboot and try now and then edit the post again)

[reboot done]

Well as i expected: the same key now has the values [us altgr-intl,us intl] ! How upseting.

This is as geeky i have ever been in my life, so i definitely need help (and if this is a common issue for others too, it should be filed as a bug in my opinion)

Thanks!

---

### Post by VH-BIL on 2010-06-24
Im not sure but I will try and help. Have a look at the "/etc/default/console-setup" file and the XKBLAYOUT describes the keyboard layout.
here is mine:
```
# A configuration file for setupcon

# Change to "yes" and setupcon will explain what is being doing
VERBOSE_OUTPUT=no

# Setup these consoles.  Most people do not need to change this.
ACTIVE_CONSOLES="/dev/tty[1-6]"

# Put here your encoding.  Valid charmaps are: UTF-8 ARMSCII-8 CP1251
# CP1255 CP1256 GEORGIAN-ACADEMY GEORGIAN-PS IBM1133 ISIRI-3342
# ISO-8859-1 ISO-8859-2 ISO-8859-3 ISO-8859-4 ISO-8859-5 ISO-8859-6
# ISO-8859-7 ISO-8859-8 ISO-8859-9 ISO-8859-10 ISO-8859-11 ISO-8859-13
# ISO-8859-14 ISO-8859-15 ISO-8859-16 KOI8-R KOI8-U TIS-620 VISCII
CHARMAP="UTF-8"

# The codeset determines which symbols are supported by the font.
# Valid codesets are: Arabic Armenian CyrAsia CyrKoi CyrSlav Ethiopian
# Georgian Greek Hebrew Lao Lat15 Lat2 Lat38 Lat7 Thai Uni1 Uni2 Uni3
# Vietnamese.  Read README.fonts for explanation.
CODESET="Lat15"

# Valid font faces are: VGA (sizes 8, 14 and 16), Terminus (sizes
# 12x6, 14, 16, 20x10, 24x12, 28x14 and 32x16), TerminusBold (sizes
# 14, 16, 20x10, 24x12, 28x14 and 32x16), TerminusBoldVGA (sizes 14
# and 16), Fixed (sizes 13, 14, 15, 16 and 18), Goha (sizes 12, 14 and
# 16), GohaClassic (sizes 12, 14 and 16).
FONTFACE="VGA"
FONTSIZE="16"

# You can also directly specify nonstandard font and ACM to load:
# FONT=/usr/local/share/funnyfonts/sarge16.psf
# ACM=/usr/local/share/consoletrans/my_special_encoding.acm

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""


# Do not update the following md5 sum if you change
# /etc/console-setup/boottime.kmap.gz and Debconf will not overwrite
# your custom keymap.  Do not update it even if you want to make
# Debconf overwrite it.  Instead simply specify the empty string as
# a md5 sum.

BOOTTIME_KMAP_MD5="aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
```

---

### Post by jesuisbenjamin on 2010-06-24
Well it provides only one keyboard details (the one i need) 

```
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="intl"
XKBOPTIONS="lv3:ralt_switch"
```

But then why do i have an alternative keyboard showing up?:-k

---

### Post by VH-BIL on 2010-06-24
Just an idea, The keyboard application is in preferences and not administration so there must be a place that it stores the keyboard layout in your home directory as well. Just on a search I did them I found something you may want o check out "/home/user/.gconf/desktop/gnome/peripherals/keyboard/kbd/%gconf.xml" (change user to your username). If not there have a look somewhere in your "hidden" directories and file in your home directory.

Let me know how you go...

---

### Post by jesuisbenjamin on 2010-06-24
Hi thanks! 

I didn't know about the preference~/home relation.

I found the file you mentioned and it contains: [PHP]
<gconf>
	<entry name="options" mtime="1277376877" type="list" ltype="string">
		<li type="string">
			<stringvalue>lv3	lv3:ralt_switch</stringvalue>
		</li>
		<li type="string">
			<stringvalue>grp	grp:alts_toggle</stringvalue>
		</li>
	</entry>
	<entry name="layouts" mtime="1277411184" type="list" ltype="string">
		<li type="string">
			<stringvalue>us	altgr-intl</stringvalue>
		</li>
		<li type="string">
			<stringvalue>us	intl</stringvalue>
		</li>
	</entry>
</gconf>[/PHP]

Now i am going to try the following part:
[PHP]<li type="string">
			<stringvalue>us	intl</stringvalue>
		</li>[/PHP]

Let's hope it works, i'll do that, reboot and reply.

---

### Post by jesuisbenjamin on 2010-06-24
Haha!
It didn't work!
The code is back to what it was before :)

What's the point of code if it re-write itself! :-k

---

### Post by VH-BIL on 2010-06-24
Mine says 

```
<?xml version="1.0"?>
<gconf>
	<entry name="model" mtime="1274248721" type="string">
		<stringvalue>pc105</stringvalue>
	</entry>
	<entry name="layouts" mtime="1257066097" type="list" ltype="string">
		<li type="string">
			<stringvalue>us</stringvalue>
		</li>
	</entry>
</gconf>
```

Try changing it to that (back up yours first).

---

### Post by jesuisbenjamin on 2010-06-25
Hi there,

By doing this, after booting up, i have US and the famous US intl is added up.
So regardless of any change in the gconf.xml the US intl adds up to the list of layouts, whatever may be in the list.

NB: when i change the xml file and save, then the window-decorator (i guess the whole of Compiz) crashes. I wonder how that is related.

Thanks for your help so far.

PS: i reckon there is another file from which the keyboard preference chosen during install is copied and added to the "live" keyboard-preference. The question is to find out which one.

---

### Post by VH-BIL on 2010-06-25
all my searches for you seem to point towards "/etc/X11/xorg.conf" or "/etc/default/console-setup" (on Ubuntu 10.04 it would be console-setup).

---

### Post by jesuisbenjamin on 2010-06-25
Ha! 
i looked for this xorg.conf but couldn't find it, so imma look for the second.

Thanks

---

### Post by jesuisbenjamin on 2010-06-25
Oh i see,

i did see the second (/etc/default/console-setup) but there is but one keyboard mentioned there (the one i need) whereas the keyboard that is added up is not listed in that file.

it must be somewhere else.

---

### Post by VH-BIL on 2010-06-25
> **jesuisbenjamin said:**
> Ha! 
i looked for this xorg.conf but couldn't find it, so imma look for the second.

Thanks

If it is not the you can create one by:
```
sudo Xorg -configure
```

---

### Post by jesuisbenjamin on 2010-06-25
Hi,

it returns:

```
Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

```

:cry:


After removing the .X0log file and running Xorg -configure it returns:```
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```

---

### Post by VH-BIL on 2010-06-25
Try this:

Log out of X using:
```
sudo stop gdm
```

Then create the xorg.conf file with:
```
sudo  Xorg -configure
```

Copy the file to /etc/X11/xorg.conf by: (You might have to change "jesuisbenjamin" to your login name)
```
cp /home/jesuisbenjamin/xorg.conf.new  /etc/X11/xorg.conf
```

Start the X server again by:
```
sudo start gdm
```

Or reboot instead of start X by:
```
sudo reboot
```

---

### Post by jesuisbenjamin on 2010-06-25
Hi!

I can't get past step 1:
```
sudo stop gdm
```

I get a text-based interface (as in boot up / shut down) checking various status. It waits for "checking battery state..." and nothing happens further.

What is going on?

---

### Post by VH-BIL on 2010-06-25
You can switch to other terminals after you stop the gdm by using ALT + F2 or ALT + other F keys for different terminals.

---

### Post by jesuisbenjamin on 2010-06-25
Thanks.

OK it's done: xorg.conf is created.
I opened it in gedit but couldn't see any mention of keyboard layout.
What's the next step?

Cheers.

---

### Post by VH-BIL on 2010-06-25
Im not really sure im just guessing and trying to help...

Here is my xorg.conf file and the commented keyboard parts for you to check out:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 256.35  (buildmeister@builder101)  Wed Jun 16 19:25:59 PDT 2010

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#	# generated from default
#    Identifier     "Keyboard0"
#    Driver         "kbd"
#EndSection
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "keyboard"
#EndSection
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

Section "ServerLayout"

	# commented out by update-manager, HAL is now used and auto-detects devices
	# Keyboard settings are now read from /etc/default/console-setup
	#    InputDevice    "Keyboard0" "CoreKeyboard"
	# commented out by update-manager, HAL is now used and auto-detects devices
	# Keyboard settings are now read from /etc/default/console-setup
	#    InputDevice    "Mouse0" "CorePointer"
	# commented out by update-manager, HAL is now used and auto-detects devices
	# Keyboard settings are now read from /etc/default/console-setup
	#    InputDevice    "Keyboard0" "CoreKeyboard"
	# commented out by update-manager, HAL is now used and auto-detects devices
	# Keyboard settings are now read from /etc/default/console-setup
	#    InputDevice    "Mouse0" "CorePointer"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "DontZap" "False"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
	# generated from default
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by jesuisbenjamin on 2010-06-25
Ha, mine is shorter and there is nothing about keyboard layout: ```
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
	Load  "extmod"
	Load  "dbe"
	Load  "dri2"
	Load  "dri"
	Load  "glx"
	Load  "record"
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
	BoardName   "Mobile GM965/GL960 Integrated Graphics Controller"
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

---

### Post by VH-BIL on 2010-06-25
It must be in your home folder in a hidden file/folder I guess as I just changed my keyboard layout and it didn't ask me for a password to use administrator permissions.

---

### Post by jesuisbenjamin on 2010-06-25
I just looked into the /home hidden files but found nothing relevant except for the gconf file edited before... :(

It's crazy that something that ought to be simple is to difficult... (i really think 10.04 is messed up when it comes to interface and customisation)

---

### Post by VH-BIL on 2010-06-25
But just a something to think about, for the keyboard layout dialog to change the layout without a admin password it has to store the config in an area on the hard drive that the user (You) have permissions to write data.

---

### Post by jesuisbenjamin on 2010-06-25
Haaaargh!! ](*,)

I tried filing a report with ubuntu-bug but it does not recognise gnome-keyboard-properties as a valid package!

This is frustrating!
Thanks for helping.

---

### Post by jesuisbenjamin on 2010-06-25
I eventually found my way through launchpad. Hurray.

---

### Post by jesuisbenjamin on 2010-06-25
Yeah it's fixed!\\:D/


The xorg.conf file actually was the determining file.

**What should happen:** the xorg.conf overrides a default keyboard-layout setting (where this default is remains a mystery to me). If no layout option is stated, the default settings remain true.

**The problem:** changing the layout setting with gnome-keyboard-properties did not affect xorg.conf and when rebooting the default keyboard-layout is restored next tot he alternative layouts added after installation.

**Solution: **
Change the keyboard section in xorg.conf so it looks like this:
```
Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "Xkblayout" "us altgr-intl"	
EndSection
```

In the above the line:
```
Option   "Xkblayout"
```
is responsible for the layouts, in this case the "us altgr-intl" is the only layout. Alternatively, you could have "us, fr, ur" for US layout, French and Urdu.

Thanks to thread [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=5985416](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=5985416) and VH-BIL! ):P

**PS:** Ubuntu Team, if you give me trouble again with this keyboard stuff i'll be scolding you. But because Ubuntu really is cool stuff at 98% i'll be ready to forgive :) Would you be please so kind to fix this kinds of _basic_ issues which should not happen in a _proper_ OS?

---

### Post by simosx on 2010-06-25
Adding an xorg.conf file is the wrong way to configure the keyboard layout.
Nowdays the X server is able to work without X.Org. You find instructions for xorg.conf because that was the legacy/old way.

The correct way is to use the Keyboard preference dialog. The settings are also accesible using the gconf-editor. Do not edit the gconf files directly, as you may mess up the system.

In some cases, Ubuntu may not respect the settings you put in the Keyboard preference dialog, and your layout settings are not remembered when you restart. This used to be a bug in the beta of 10.04 though I believe it has been fixed.
The only place that has your initial (during install) configuration is indeed /etc/default/console-setup, so if your system is confused and forces to use the console-setup setting, then edit there.
It would be great to diagnose those cases (if they exist) where Ubuntu does not remember the 'gconf' setting that you put in the Keyboard preference dialog.

---

### Post by jesuisbenjamin on 2010-06-25
Hi Simosix,

Thanks for your input. As the past post reveal, i already tried to change the setting with gconf-edit, to no avail.
The /etc/default/console-setup also has been looked at: the "per-installation-default" layout was not stated there, only the one added post-installation. The conclusion was that the former layout was stated somewhere else.

I do not know what is proper and improper, but i need to fix my problem: i.e. bend the keyboard layout to my will. Lacking any other solution the last worked out. In the end i am just coping with some basic bug which in my opinion should not even exist in the 10th edition.

This said, with regard to the diagnose you mentioned, you have now a case at hand, and i am most happy to contribute by participating in a diagnose.

Let me know.

---

### Post by jesuisbenjamin on 2010-06-26
Bug has been filed; [https://bugs.launchpad.net/ubuntu/+source/kmflcomp/+bug/598475](https://bugs.launchpad.net/ubuntu/+source/kmflcomp/+bug/598475) . Many duplicates are found in launchpad, it would be good to assess the impact of this bug and what is/will be done about it.

---

### Post by simosx on 2010-06-26
> **jesuisbenjamin said:**
> Bug has been filed; [https://bugs.launchpad.net/ubuntu/+source/kmflcomp/+bug/598475](https://bugs.launchpad.net/ubuntu/+source/kmflcomp/+bug/598475) . Many duplicates are found in launchpad, it would be good to assess the impact of this bug and what is/will be done about it.

Thanks for taking the time to write the bug report. It is important to mark as dups those bug reports so that the reporters follow a common report.

I remember seeing a bug report on launchpad during the alpha versions of lucid, which talked about the keyboard settings disappearing on reboot. It was a long report with many replies.

The concern here is to get some instructions on how to properly reproduce this issue.
Is the problem with
1. the user configuring as default a keyboard layout other than US English, which would potentially not allow you to type your username during reboot at the login screen (gdm)?
2. all faulty cases have to do with installations of an Alpha version of Ubuntu which has been updated incrementally to the final 10.04?
3. something else?

(The offending package should be either gdm, gnome-settings-xyz, libgnomekdb).

---

### Post by jesuisbenjamin on 2010-06-26
I suppose that if i removed the xkbdlayout options from the xorg.conf file, the issue would be true again.

Now the issue is not so much when logging-in, although this was true for my case only since i struggled between US Intl and US AltGr-Intl, so the difference is not huge.

During the process i also tried to alter the added keyboard layout as US (plain) and it did not make a difference. It may possibly be in due to the layout to the layout set up during install but i could not be sure since that is the variable i cannot change.

I noticed in Launchpad that the issue was already existing in 9.10 (which i haven't used). I installed 10.04 few days ago and ran updates, if there was an update correcting this bug, could have i had a version in which the bug was still existent?

I suspect there are more duplicates out there.

---

### Post by VH-BIL on 2010-06-28
It is fixed, that is the main thing.

---

### Post by AZorin on 2010-10-05
Hello, I'm also having this problem and I need to find out how to fix it in the default setting files.
Thanks in advance!

---

