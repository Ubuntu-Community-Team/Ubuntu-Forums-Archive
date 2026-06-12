---
title: "Stuck with 800x600 display resolution"
date: 2011-03-02
forum: General Help
---

### Post by prasoon938 on 2011-03-02
Hi All,

I am using Ubuntu 10.10. I am facing a problem with display resolution. My monitor is a 14" Samtron (56v) and with Ubuntu i am stuck with 800x600 resolution. I tried everything from 'xrandr' to 'sudo dpkg-reconfigure -phigh xserver-xorg' so that i can have 1024x768 resolution. But it seems that nothing is working out. Please help.........

Thanks in advance....

---

### Post by Dans564 on 2011-03-02
what driver and video card do u have.  Post the output of ```
lspci
```

---

### Post by Mariane on 2011-03-02
Is it a new install or did it happen after 10.10 was installed? 

If it's a new install you can try installing 10.04 and then upgrading to 10.10. Save a copy of xorg.conf from 10.04. 

Mariane

---

### Post by colin.p on 2011-03-02
> **prasoon938 said:**
> Hi All,

I am using Ubuntu 10.10. I am facing a problem with display resolution. My monitor is a 14" Samtron (56v) and with Ubuntu i am stuck with 800x600 resolution. I tried everything from 'xrandr' to 'sudo dpkg-reconfigure -phigh xserver-xorg' so that i can have 1024x768 resolution. But it seems that nothing is working out. Please help.........

Thanks in advance....

On my old athlon 1800+ server, using lucid, I just did an update, and I wasn't paying too much attention as to what was updating. I know it was a kernel update and samba, but don't know what else.
On rebooting, the display (nVidia 6200) was stuck in 640X480 and a couple of half-hearted attempts to fix failed. I then did the "old standby" and rebooted again. Voila, back into 1024X768.
So the moral of the story, try a reboot, but you already knew that.

---

### Post by prasoon938 on 2011-03-03
Thanks you guys...

This is a new install. As i am having a slow internet connection, downloading 10.4 would take ages for me... but i would still keep that as my last option.

The output of 'lspci' is as follows


00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:01.0 Multimedia audio controller: Yamaha Corporation YMF-724F [DS-1 Audio Controller] (rev 03)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by prasoon938 on 2011-03-06
Hi guys,

Thanks for all the help provided... After much effort i finally got it working...

The problem was that; there was no xorg.conf file inside my /etc/X11 directory.

For anybody who is stuck with the same problem - please follow the instructions mentioned in this link [http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

This will create the xorg.conf file in your /etc/X11 directory. Restart the computer, and then check Monitor configuration. you will see that all supporting resolutions had been added there....

---

### Post by Chris Kupka on 2011-03-13
Hey everyone,

I'm having the same problem on a Dell inspiron mini 10.  Should have 1024x600 resolution, but instead I'm only getting 800x600.  I've tried ARandR and xrandr, but they didn't work.  I tried the above-posted fix (i.e., creating an xorg.conf file in /etc/X11, but when I do so it won't allow me to restart the GDM.  I do have xorg.conf.new in my home folder.  I'm guessing that some of the values must be incorrect?  When I tried screwing around w/ xorg.conf in Jaunty I had a huge headache on my hands.

Here's what's in xorg.conf.new:
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
	Load  "record"
	Load  "dri2"
	Load  "extmod"
	Load  "glx"
	Load  "dri"
	Load  "dbe"
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
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card0"
	Driver      "fbdev"
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


Here's the output for lspci:

```

00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```

Any help would be appreciated.

---

### Post by billcauley on 2011-03-13
Worked for me!  Though I don't have the sharpness that I had in the previous Ubuntu version, my monitor is now detected, and I can select resolutions and refresh rates.  Thanks.

---

