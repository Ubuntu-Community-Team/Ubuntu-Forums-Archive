---
title: "Configure two X screen in two monitor mode (12.04,Intel GPU,rdesktop)"
date: 2012-07-24
forum: General Help
---

### Post by The_ERROR on 2012-07-24
Hi,

I have problem with rdesktop which in fullscreen mode span over all two monitors, but I need/want to span only on one of them. A read several [discussion about]("http://ubuntuforums.org/showthread.php?t=1274217") this and looks, that my problem is that I'm having configured one X screen showed on both monitor.

Could somebody help me with this xorg.conf configuration?

Dell Latitude 6520, Ubuntu 12.04


lspci:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 6 Series/C200 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
0a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. 1394 OHCI Compliant Host Controller (rev 05)
0a:00.1 SD Host controller: O2 Micro, Inc. Integrated MMC/SD controller (rev 05)
0a:00.2 Mass storage controller: O2 Micro, Inc. O2 Flash Memory Card (rev 05)
```

actual xorg.conf:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#	InputDevice    "Mouse0" "CorePointer"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#	InputDevice    "Keyboard0" "CoreKeyboard"
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
	Load  "glx"
	Load  "record"
	Load  "dri2"
	Load  "dri"
	Load  "dbe"
	Load  "extmod"
EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#	Identifier  "Keyboard0"
#	Driver      "kbd"
#EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#	Identifier  "Mouse0"
#	Driver      "mouse"
#	Option	    "Protocol" "auto"
#	Option	    "Device" "/dev/input/mice"
#	Option	    "ZAxisMapping" "4 5 6 7"
#EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
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

### Post by dino99 on 2012-07-24
keep in mind that actual kernel directly deal with X, so your xorg.conf (very oldish style) confuse it. Rename it and reboot

---

### Post by The_ERROR on 2012-07-24
Thanks for tip... 

I removed xorg.conf than. Seems, that it do not stopped working - so it is fine, but seems, that there is still used one xscreen, so there is still same problem.

I used Remmina before, but there is some bug probably in compiz which made using of Remmina because of really annoying bug - it is [jumping across worspaces]("https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/980766").

I'm still having fullscreen of rdesktop spanned across both monitors :(

```
user@hostname:~$ xrandr -q
Screen 0: minimum 320 x 200, current 3360 x 1050, maximum 8192 x 8192
LVDS1 connected (normal left inverted right x axis y axis)
   1920x1080      60.0 +   59.9     40.0  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI3 connected 1680x1050+1680+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)

```

---

### Post by dino99 on 2012-07-24
Sadly i've no experience with Intel drivers, but there are some bugs opened

[https://www.google.com/search?hl=fr&output=search&sclient=psy-ab&q=ubuntu+pubkey&btnG=#hl=fr&sclient=psy-ab&q=+intel+xorg+precise+dual+screen&oq=+intel+xorg+precise+dual+screen&gs_l=serp.3...5331.9846.2.10217.12.12.0.0.0.0.141.933.11j1.12.0...0.0...1c.pXiZ5PMm7As&pbx=1&fp=1&biw=1483&bih=819&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&cad=b&sei=45IOUKnLD4SnhAerkYCgAw](https://www.google.com/search?hl=fr&output=search&sclient=psy-ab&q=ubuntu+pubkey&btnG=#hl=fr&sclient=psy-ab&q=+intel+xorg+precise+dual+screen&oq=+intel+xorg+precise+dual+screen&gs_l=serp.3...5331.9846.2.10217.12.12.0.0.0.0.141.933.11j1.12.0...0.0...1c.pXiZ5PMm7As&pbx=1&fp=1&biw=1483&bih=819&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&cad=b&sei=45IOUKnLD4SnhAerkYCgAw)

---

### Post by The_ERROR on 2012-07-24
By these bugs seems, that I should shut up, and be happy that my dual monitors working "somehow" fine :)

Maybe it is because of virtual desktop and somehow "incopatible" mode of it... Question is, if it is possible to reach those two separate Xscreens or not.

---

