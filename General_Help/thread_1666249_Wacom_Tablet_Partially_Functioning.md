---
title: "Wacom Tablet Partially Functioning"
date: 2011-01-13
forum: General Help
---

### Post by -Fenrir on 2011-01-13
OS: Xubuntu 10.10
Kernel: 2.6.35-24-generic.
Tablet: Wacom Bamboo Pen & Touch, model no. CTH-460

I'm trying to get my new Wacom tablet running. I compiled and installed xf86-input-wacom-0.10.10 and input-wacom-0.10.10-1, as I have kernel version 2.6.35 and X version 1.9.0. I have the following in my xorg.conf file.

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    # For non-LCD tablets only
        InputDevice    "pad"   # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
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
	Load  "glx"
	Load  "dbe"
	Load  "record"
	Load  "dri"
	Load  "dri2"
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

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "cursor"
  Option        "USB"           "on"                  # USB ONLY
EndSection

# This section is for USB Bamboo with touch
Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom-touch"    # USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection


Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "nvidia"
	BusID       "PCI:0:13:0"
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

My [FONT="Lucida Console"]/etc/udev/rules.d/10-local.rules[/FONT] file contains the following.

```
BUS=="usb", KERNEL=="event*", SYSFS{bInterfaceNumber}=="00", ENV{WACOM_TYPE}="stylus"
BUS=="usb", KERNEL=="event*", SYSFS{bInterfaceNumber}=="01", ENV{WACOM_TYPE}="touch"

BUS=="usb", KERNEL=="event*", SYSFS{idVendor}=="056a", ENV{WACOM_TYPE}!="touch", SYMLINK+="input/wacom"
BUS=="usb", KERNEL=="event*", SYSFS{idVendor}=="056a", ENV{WACOM_TYPE}=="touch", SYMLINK+="input/wacom-touch"
```

The touch moves my mouse, but it jumps around sometimes. The pen doesn't work. The tablet seems to be recognized by GIMP version 2.6.10, as it shows the "Wacom BambooPT 2FG 4x5 Pen eraser", "Wacom BambooPT 2FG 4x5 Pen stylus", "Wacom BambooPT 2FG 4x5 Finger pad", "Wacom BambooPT 2FG 4x5 Finger touch", in both "Preferences" -> "Input Devices" -> "Configure extended input devices..." and the "Device Status" dialog, but only the finger touch seems to work.

I also have a USB mouse plugged in. If I keep the tablet plugged in when I boot up, the mouse and touch work fine, but, if I remove the tablet and plug it back in, the mouse stops working.

With the tablet plugged in at boot up...
The **lsusb** command yields the following.

```
Bus 002 Device 004: ID 045e:0023 Microsoft Corp. Trackball Optical
Bus 002 Device 003: ID 056a:00d6 Wacom Co., Ltd 
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

**more /proc/bus/input/devices** yields the following.

```
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 
B: EV=120013
B: KEY=10000 c0200 0 0 0 0 0 700f 2000003 3803078 f830f401 febfffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=056a Product=00d6 Version=0111
N: Name="Wacom BambooPT 2FG 4x5 Pen"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.0/input/input3
U: Uniq=
H: Handlers=mouse0 event3 
B: EV=b
B: KEY=1c03 0 0 0 0 0 0 0 0 0 0
B: ABS=100 1000003

I: Bus=0003 Vendor=056a Product=00d6 Version=0111
N: Name="Wacom BambooPT 2FG 4x5 Finger"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.1/input/input4
U: Uniq=
H: Handlers=mouse1 event4 
B: EV=1b
B: KEY=6420 0 f 0 0 0 0 0 0 0 0
B: ABS=100 100001b
B: MSC=1

I: Bus=0003 Vendor=045e Product=0023 Version=0100
N: Name="Microsoft Microsoft Trackball Optical®"
P: Phys=usb-0000:00:02.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input5
U: Uniq=
H: Handlers=mouse2 event5 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

```

Changing **Option "Device" "/dev/input/mice"** to **Option "Device" "/dev/input/mouse0"** in xorg.conf makes the tablet's touch stop working, so I expect it might just be recognized as another mouse, but I still don't know why the pen doesn't work.

I'm hoping that I'm not missing something glaringly obvious here. It took me a few hours to realize that I had been using the wrong drivers, so I'm obviously not the most perceptive sort.

---

### Post by Favux on 2011-01-13
Hi -Fenrir,

If you installed xf86-input-wacom-0.10.10 from the tar that's the problem.  It has a known bug for the pad and more importantly hasn't added your model number yet.  So while the kernel driver wacom.ko has your model the X driver doesn't.  See the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

You do not need to use the xorg.conf, the default 50-wacom.conf in xorg.conf.d should be fine.  If you want to use the xorg.conf you can remove the "SendCoreEvents" in "Server Layout".  It has been deprecated since X server 1.7.  Also you should change cursor to touch.  The cursor refers to a Wacom tablet mouse/puck.  In addition the symlink for pad and touch is 'wacom-touch' not 'wacom' provided you have the right udev rules.  It looks like you do.  Did you add a line for your model?

Hope this is helpful.

---

### Post by -Fenrir on 2011-01-13
> **Favux said:**
> Hi -Fenrir,

If you installed xf86-input-wacom-0.10.10 from the tar that's the problem.  It has a known bug for the pad and more importantly hasn't added your model number yet.  So while the kernel driver wacom.ko has your model the X driver doesn't.  See the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

I tried installing the linuxwacom-0.8.8-10 in the beginning, but the tablet didn't work at all. It didn't even show up in /proc/bus/input/devices. Does this mean that I need input-wacom-0.10.10 but not xf86-input-wacom-0.10.10? I'm sorry if that is a stupid question, as I have only a vague idea of what I'm doing here.
> 
In addition the symlink for pad and touch is 'wacom-touch' not 'wacom' provided you have the right udev rules.  It looks like you do.  Did you add a line for your model?

I hadn't added a line for my model. I noticed that the drivers contain a rules file in the utils directory. Should I just use that one? or do I need to learn how to add a line for my model? (Learning shouldn't be hard; I think I understand how they work.)

Thanks for trying to help me.

---

### Post by Favux on 2011-01-13
The linuxwacom 0.8.8-10 wacom.ko (the usb kernel driver) does not have your model in it.  You'd have to manually add it as described in the mini HOW TO on adding new models in post #2 of the HOW TO thread.  The input-wacom 0.10.10-1 is the first wacom.ko that has your model added.  That's why it's working for you without having to manually patch it.

The xf86-input-wacom is the X driver.  It takes the raw usb data the wacom.ko feeds it and then converts it into output the X window system (the thing that draws the gui) understands.  That wacom driver still doesn't have your model.  So you have to follow the part in post #2 for it.

The line you add would be something like:
```
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00d6", SYMLINK="input/tablet-wacom-bamboo-p&t-K-4x5-$env{WACOM_TYPE}"
```

---

### Post by Favux on 2011-01-13
Sorry about the double post.  Either the server is acting up again or my ISP is.

---

### Post by -Fenrir on 2011-01-13
I'm very sorry. I neglected to check the entire thread before posting.

My Wacom tablet is working well now. Thank you **very** much for your advice and patience.

---

### Post by Leovi on 2011-01-14
My tablet run Android 2.1 OS and I want to reboot it to install Android 2.2 and enter the official market. Unfortunately, the manufacturer hasn't release the firmware yet. So, if I reboot my tablet with third party firmware, it would be safe? 
The specs. of my tablet is [**[COLOR="Red"]here[/COLOR]**]("http://www.****************/touch-screen-android-21-apad-style-tablet-pc-101-inch-with-rj45-interface-support-two-tf-cards-and-wifi-360-degree-menu-rotate-p-1541.html")(a Chinese store) where I got it two months ago.

---

