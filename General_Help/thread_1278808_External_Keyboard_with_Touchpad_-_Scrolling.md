---
title: "External Keyboard with Touchpad - Scrolling"
date: 2009-09-30
forum: General Help
---

### Post by Loan_Refi on 2009-09-30
I have a Dell Inspiron 300m Laptop runing Ubuntu 8.04 Hardy Kernel Linux 2.6.24-24-generic

I bought an External Keyboard with touchpad built in but.  I bout it with the intention to use the touchpad scrolling feature. Same way I use the laptop's touchpad.

Well Scrolling is the only feature that doesn't work. I tried modifying the  xorg.conf but it didn't work.

I followed some other examples from old threads here but it just doesn't work for me.

The keyboard is this; 

[http://www.solidtekusa.com/mini.htm#KB3910](http://www.solidtekusa.com/mini.htm#KB3910)

KB-3910

Brief:
Slim and elegant design for convenient usage
Multi-Lingual available
Touchpad as a pointing device with scroll up and down function
LED for Caps_Lock, Scrl_lock; and Num_lock

Detailed Information:
- Key: 88/89 keys
- Key pitch: 19.05mm
- Switch Travel: 3.5 +/-0.5 mm
- Switch Reliability: 5 million cycles
- Keyboard dimension: 291 x 197 x 29 mm (LxWxH)
- Switch mechanism: Membrane
- Standard Notebook used Touchpad with L and R mouse buttons

Specification:
- Compliance to USB 1.1 spec
- Power consumption: +5VDC +/- 5% @ 100mA
- Agency Approvals: FCC&#12289;CE&#12289;BSMI
- Operating temperature: 0 degree C ~+50 degree C
- Storage temperature: -20 degree C ~+65 degree C

My xorg.conf is this;
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option          "SHMConfig"             "on"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

cat /proc/bus/input/devices

I: Bus=0003 Vendor=0dc6 Product=3412 Version=0100
N: Name="USB keyboard"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input10
U: Uniq=
H: Handlers=kbd event10 
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=0dc6 Product=3412 Version=0100
N: Name="USB keyboard"
P: Phys=usb-0000:00:1d.0-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.1/input/input11
U: Uniq=
H: Handlers=mouse2 event11 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

If someone has this keyboard working with scrolling please help me out or if some one knows how to make this keyboard work with vertical scrolling please help out.

Thanks!

---

### Post by fragos on 2009-09-30
I have a USB touchpad that lsusb shows as:

Bus 001 Device 007: ID 0488:0020 Cirque Corp.

I works completely without any settings in xorg.conf. You might try looking at the Configuration Editor: desktop-> gnome-> peripherals-> mouse. There are check boxes there for pad scrolling.

---

### Post by Loan_Refi on 2009-09-30
I did that already;

>System>Preferences>Mouse

I have checked;
General
Enable Touchpad
Enable mouse clicks with touchpad
Scrolling
Enable Vertical Scrolling

with the above settings scrolling is not working.

---

### Post by fragos on 2009-09-30
The Preferences you checked offer a subset of actual parameters. The full list is available when you run the Configuration Editor. To see the Config Editor you may need to right click Applications and select Edit Menus. Select System Tools and check the box for Configuration Editor. You will then have access to the Configuration Editor in Menu under System Tools.

---

### Post by Loan_Refi on 2009-09-30
Oh, I understand now. Yes its there, I will try it once I get back to the computer with the issue.

Will report back,
Thank you for your help!!!

---

### Post by Loan_Refi on 2009-09-30
okay, this time I went to the right place.

There is a kbd & mouse I think kbd is my keyboard with the touchpad built in.

The mouse option is listed but already has scrolling enabled "pad_vert_scroll" checked!

I don't know what else to check or change.  I may need to return the keyboard since I can't use the scroll feature.

I really like would like to use it the same way I use the laptops touchpad because I can scroll easily in terminal and everything else.

Thanks!

---

### Post by alroger on 2010-08-19
Loan, did you ever get it working?

---

