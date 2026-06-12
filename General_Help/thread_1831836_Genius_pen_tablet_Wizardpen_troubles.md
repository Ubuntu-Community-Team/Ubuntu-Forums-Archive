---
title: "Genius pen tablet Wizardpen troubles"
date: 2011-08-23
forum: General Help
---

### Post by unused_bagels on 2011-08-23
Every time I install wizardpen, my mouse sits at the top left corner of the screen.  I can use the pen just fine as a cursor, but it isn't pressure sensitive.  I tried following tutorials, but they didn't work out.  I think I'm doing something wrong somewhere, but I can't figure out what.  I can provide any extra information as needed.

---

### Post by Favux on 2011-08-24
Hi unused_bagels,

What release of Ubuntu are you using?

Usually when the cursor is stuck in the left upper corner that means that X isn't getting any coordinate information from a X driver.  The left upper corner is 0,0.

Let's find out which tablet you have.  Enter in a terminal:
```
xinput list
```
and post the output.

The pen/stylus is probably on the evdev X driver which is why it doesn't have pressure.  So the tablet also came with a tablet mouse?

---

### Post by unused_bagels on 2011-08-24
xxxx@Mr-Hooper:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                 	id=8	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                 	id=9	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; zc3xx                                   	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

I'm using Natty, and yes, my tablet also came with a mouse (which is also magnetic)

---

### Post by Favux on 2011-08-24
Alright.  Let's check out what X driver is being used.  Post the outputs of:
```
xinput list-props 8
and
xinput list-props 9
```
Did you install the Wizardpen driver through Software Center or Synaptic Package Manager or did you use the PPA?  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=](https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=)

You should have a 70-wizardpen.conf file in /usr/share/X11/xorg.conf.d.  Please post the contents.

---

### Post by unused_bagels on 2011-08-24
> xxxxx@Mr-Hooper:~$ xinput list-props 8
Device 'UC-LOGIC Tablet WP8060U':
	Device Enabled (121):	1
	Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (239):	0
	Device Accel Constant Deceleration (240):	1.000000
	Device Accel Adaptive Deceleration (241):	1.000000
	Device Accel Velocity Scaling (242):	10.000000
xxxxx@Mr-Hooper:~$ xinput list-props 9
Device 'UC-LOGIC Tablet WP8060U':
	Device Enabled (121):	1
	Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (239):	0
	Device Accel Constant Deceleration (240):	1.000000
	Device Accel Adaptive Deceleration (241):	1.000000
	Device Accel Velocity Scaling (242):	10.000000

> Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag "wizardpen"
   Driver "wizardpen"
   Option		"TopX"		"1506"
   Option		"TopY"		"2705"
   Option		"BottomX"	"31225"
   Option		"BottomY"	"30892"
EndSection
I installed through synaptic.

---

### Post by Favux on 2011-08-24
Where did those coordinates come from?  Were they already there?  Let's try changing it to:
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
first.  Use:
```
gksudo gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```

---

### Post by unused_bagels on 2011-08-24
those coord. were already there.  The new conf text didn't change anything.

---

### Post by Favux on 2011-08-24
Let's see if we can do without the coordinates for now.

Did you reboot?  It should have turned the mouse off which would hopefully give the pen pressure.

If you did reboot we could look at the Xorg.0.log in /var/log.  Right click on it to compress it (Create Archive) and attach it to your next post with Manage Attachments below.

---

### Post by unused_bagels on 2011-08-24
No mouse, and no pressure sensitivity.  Just a pen.  Here's the log.

---

### Post by Favux on 2011-08-24
OK, some progress.  For some reason you are getting duplicate pens, it looks like.  And the second one on event4 is wrong.  It has the wrong coordinates and thinks z is 0 which is why you would have no pressure.
```
[    19.304] (II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/event3)
[    19.304] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev tablet catchall"
[    19.304] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "WizardPen class"
[    19.304] (II) LoadModule: "wizardpen"
[    19.304] (II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
[    19.305] (II) Module wizardpen: vendor="X.Org Foundation"
[    19.305] 	compiled for 1.10.1, module version = 0.8.1
[    19.305] 	Module class: X.Org XInput Driver
[    19.305] 	ABI class: X.Org XInput driver, version 12.3
[    19.305] (II) Using input driver 'wizardpen' for 'UC-LOGIC Tablet WP8060U'
[    19.305] (II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
[    19.305] (**) UC-LOGIC Tablet WP8060U: always reports core events
[    19.305] (**) Option "Device" "/dev/input/event3"
[    19.310] (--) UC-LOGIC Tablet WP8060U: MaxX:32767 MaxY:32767 MaxZ:1023
[    19.310] (--) UC-LOGIC Tablet WP8060U: aspect ratio:0.00:1
[    19.310] (**) UC-LOGIC Tablet WP8060U is in absolute mode
[    19.310] (**) UC-LOGIC Tablet WP8060U: TopX not set, defaulting to "5%"
[    19.310] (**) UC-LOGIC Tablet WP8060U: TopY not set, defaulting to "5%"
[    19.310] (**) UC-LOGIC Tablet WP8060U: BottomX not set, defaulting to "95%"
[    19.310] (**) UC-LOGIC Tablet WP8060U: BottomY not set, defaulting to "95%"
[    19.310] (II) UC-LOGIC Tablet WP8060U: ScreenX = 1600, ScreenY = 900
[    19.310] (**) UC-LOGIC Tablet WP8060U: TopX                   = 1638
[    19.310] (**) UC-LOGIC Tablet WP8060U: TopY                   = 1638
[    19.310] (**) UC-LOGIC Tablet WP8060U: BottomX                = 31128
[    19.310] (**) UC-LOGIC Tablet WP8060U: BottomY                = 31128
[    19.310] (**) UC-LOGIC Tablet WP8060U: TopZ    (min pressure) = 0
[    19.310] (**) UC-LOGIC Tablet WP8060U: BottomZ (max pressure) = 1023
[    19.310] (**) UC-LOGIC Tablet WP8060U: always reports core events
[    19.320] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input3/event3"
[    19.320] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP8060U" (type: WizardPen Tablet)
[    19.320] (II) UC-LOGIC Tablet WP8060U Increment: 20
[    19.320] (**) UC-LOGIC Tablet WP8060U: (accel) keeping acceleration scheme 1
[    19.320] (**) UC-LOGIC Tablet WP8060U: (accel) acceleration profile 0
[    19.320] (**) UC-LOGIC Tablet WP8060U: (accel) acceleration factor: 2.000
[    19.320] (**) UC-LOGIC Tablet WP8060U: (accel) acceleration threshold: 4
[    19.320] (II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/mouse0)
[    19.320] (**) UC-LOGIC Tablet WP8060U: Ignoring device from InputClass "WizardPen ignore mouse dev class"
[    19.320] (II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/event4)
[    19.320] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev pointer catchall"
[    19.320] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev tablet catchall"
[    19.320] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "WizardPen class"
[    19.320] (II) Using input driver 'wizardpen' for 'UC-LOGIC Tablet WP8060U'
[    19.320] (II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
[    19.320] (**) UC-LOGIC Tablet WP8060U: always reports core events
[    19.320] (**) Option "Device" "/dev/input/event4"
[    19.320] (--) UC-LOGIC Tablet WP8060U: MaxX:32767 MaxY:28 MaxZ:0
[    19.320] (--) UC-LOGIC Tablet WP8060U: aspect ratio:0.00:1
[    19.320] (**) UC-LOGIC Tablet WP8060U is in absolute mode
[    19.320] (**) UC-LOGIC Tablet WP8060U: TopX not set, defaulting to "5%"
[    19.320] (**) UC-LOGIC Tablet WP8060U: TopY not set, defaulting to "5%"
[    19.320] (**) UC-LOGIC Tablet WP8060U: BottomX not set, defaulting to "95%"
[    19.320] (**) UC-LOGIC Tablet WP8060U: BottomY not set, defaulting to "95%"
[    19.320] (II) UC-LOGIC Tablet WP8060U: ScreenX = 1600, ScreenY = 900
[    19.320] (**) UC-LOGIC Tablet WP8060U: TopX                   = 1638
[    19.320] (**) UC-LOGIC Tablet WP8060U: TopY                   = 1
[    19.320] (**) UC-LOGIC Tablet WP8060U: BottomX                = 31128
[    19.320] (**) UC-LOGIC Tablet WP8060U: BottomY                = 26
[    19.320] (**) UC-LOGIC Tablet WP8060U: TopZ    (min pressure) = 0
[    19.320] (**) UC-LOGIC Tablet WP8060U: BottomZ (max pressure) = 0
[    19.320] (**) UC-LOGIC Tablet WP8060U: always reports core events
[    19.320] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input4/event4"
[    19.320] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP8060U" (type: WizardPen Tablet)
[    19.320] (II) UC-LOGIC Tablet WP8060U Increment: 1
[    19.320] (**) UC-LOGIC Tablet WP8060U: (accel) keeping acceleration scheme 1
[    19.320] (**) UC-LOGIC Tablet WP8060U: (accel) acceleration profile 0
[    19.320] (**) UC-LOGIC Tablet WP8060U: (accel) acceleration factor: 2.000
[    19.320] (**) UC-LOGIC Tablet WP8060U: (accel) acceleration threshold: 4
[    19.321] (II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/mouse1)
[    19.321] (II) No input driver/identifier specified (ignoring)
```
Let's try specifying the event #.  So change:
```
    MatchDevicePath "/dev/input/event*"

```
to
```
    MatchDevicePath "/dev/input/event3"

```
and see if that gives you pressure.

---

### Post by unused_bagels on 2011-08-24
Progress.  Now I have mouse functionality, but no pen.  I can deal with that in the interim.  My wife would kill me if there were no mouse in the morning.  She's already resistant to ubuntu, I'm trying to make it easy for her.:mrgreen:

---

### Post by Favux on 2011-08-24
Interesting.  That seems to be suggesting the mouse is event3 and the stylus event4?  Bizarre.

Not many folks have a UC-LOGIC tablet mouse, I think that may be new.  So we may be running into a problem where the kernel driver/module or maybe the Wizardpen X driver doesn't work.  I don't think the Wizardpen driver actually supports a mouse yet.

So what to do?  At some point you could try the PPA driver and see if that makes a difference.  Let's work with what we have some more first.

A z axis zero would seem to be a mouse i.e. no pressure and the z axis 1023 would seem to have to be the stylus.  So what if the Wizardpen driver doesn't handle the mouse?  Should we block it or try assigning it to evdev and see if the evdev X driver can handle the tablet mouse?  Unfortunately there doesn't seem to be a way to distinguish between the two using keywords.  The kernel is exporting both as "UC-LOGIC Tablet WP8060U".  So try adding a new snippet:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/event3"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen mouse class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/event4"
    Driver "evdev"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
We're just checking what works because event # can change with hot plugging.  So we would have to use something more permanent, probably the by-path.

---

### Post by unused_bagels on 2011-08-25
everything's exactly the same.  Mouse is fine, pen is in the corner.

---

### Post by Favux on 2011-08-25
Alright, say I got the events backwards.  What happens if you swap event3 and event4 in the two snippets?

---

### Post by unused_bagels on 2011-08-25
/that took me back to no mouse, and hell if i know if there's pressure sensitivity, i'm using inkscape and no change.  pen is a nice pointer, though :/

---

### Post by Favux on 2011-08-25
OK, let's look at the *xinput list* and the Xorg.0.log with that .conf and see if we see anything different.  Any pressure in say MyPaint?

I was originally assuming the mouse would be on the mouse* event and that was what we'd want to match to evdev.

---

### Post by unused_bagels on 2011-08-25
> @Mr-Hooper:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                 	id=8	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                 	id=9	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; zc3xx                                   	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
BTW mypaint gave me pressure sensitivity, so obviously it's inkscape that's giving me the problem.  Now all i have to do is configure the mouse.

---

### Post by Favux on 2011-08-26
This is getting a little confusing.  Let's see which Product ID your tablet has.  What's the tablet line in the output of *lsusb* look like?

I looked at the deb on the PPA and don't really see anything about fixing a double entry so I'm not sure installing that will help us.

It could be the version in the repo's does not install udev rules for wizardpen tablets.    The PPA has udev rules, which are in the file 67-xorg-wizardpen.rules in /etc/udev/rules.d, after it is installed.  Can you check there or in /lib/udev/rules.d and see if the repository package installs wizardpen rules?  If you have one could you post it?

Let's also see if we can gather some more information.  Please post the output of the following:
```
udevadm info -a -p $(udevadm info -q path -n /dev/input/event3)
and
udevadm info -a -p $(udevadm info -q path -n /dev/input/event4)
```

---

### Post by unused_bagels on 2011-08-27
```
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input3/event3':
    KERNEL=="event3"
    SUBSYSTEM=="input"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input3':
    KERNELS=="input3"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{name}=="UC-LOGIC Tablet WP8060U"
    ATTRS{phys}=="usb-0000:00:02.0-3/input0"
    ATTRS{uniq}==""
    ATTRS{properties}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0':
    KERNELS=="2-3:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usbhid"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="03"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceProtocol}=="02"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{interface}=="Tablet WP8060U"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2/2-3':
    KERNELS=="2-3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="47638"
    ATTRS{idVendor}=="5543"
    ATTRS{idProduct}=="0005"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="1.5"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="2"
    ATTRS{devpath}=="3"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="UC-LOGIC"
    ATTRS{product}=="Tablet WP8060U"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="66"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="10"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.38-11-generic ohci_hcd"
    ATTRS{product}=="OHCI Host Controller"
    ATTRS{serial}=="0000:00:02.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:02.0':
    KERNELS=="0000:00:02.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ohci_hcd"
    ATTRS{vendor}=="0x10de"
    ATTRS{device}=="0x03f1"
    ATTRS{subsystem_vendor}=="0x1565"
    ATTRS{subsystem_device}=="0x3407"
    ATTRS{class}=="0x0c0310"
    ATTRS{irq}=="21"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{numa_node}=="0"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```
```
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input4/event4':
    KERNEL=="event4"
    SUBSYSTEM=="input"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input4':
    KERNELS=="input4"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{name}=="UC-LOGIC Tablet WP8060U"
    ATTRS{phys}=="usb-0000:00:02.0-3/input0"
    ATTRS{uniq}==""
    ATTRS{properties}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0':
    KERNELS=="2-3:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usbhid"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="03"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceProtocol}=="02"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{interface}=="Tablet WP8060U"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2/2-3':
    KERNELS=="2-3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="52842"
    ATTRS{idVendor}=="5543"
    ATTRS{idProduct}=="0005"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="1.5"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="2"
    ATTRS{devpath}=="3"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="UC-LOGIC"
    ATTRS{product}=="Tablet WP8060U"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="66"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="10"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.38-11-generic ohci_hcd"
    ATTRS{product}=="OHCI Host Controller"
    ATTRS{serial}=="0000:00:02.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:02.0':
    KERNELS=="0000:00:02.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ohci_hcd"
    ATTRS{vendor}=="0x10de"
    ATTRS{device}=="0x03f1"
    ATTRS{subsystem_vendor}=="0x1565"
    ATTRS{subsystem_device}=="0x3407"
    ATTRS{class}=="0x0c0310"
    ATTRS{irq}=="21"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{numa_node}=="0"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```
At this point I have no idea what's going on.  I wonder if now I can just remove the driver, reinstall it, start from scratch, and see if maybe it was just an inkscape problem.  Remember in the beginning I wasn't trying MyPaint.  I have sensitivity in MyPaint but still no dice in Inkscape.  Thoughts?
EDIT:
That still wouldn't solve my dual mouse and pen problems.

---

### Post by Favux on 2011-08-27
I'll look over the attributes walks and see if there's anything there.

Could really use the:
```
lsusb
```
output.  Knowing the product number I can look at the udev rules and code a little.  Speaking of which did you check for the udev rules?

After that, if it doesn't pan out, you might want to install the driver from the PPA.  The udev rules from that package disable the mouse but we could fix that.  We'd be checking if that package gets rid of the duplicate entry maybe due to the rules?  That might at least tell us if the mouse is suppose to be on event3 or 4 or is suppose to be on mouse*.  I think someone in the last month or so actually got their tablet mouse working.  First time I've seen that on a non-Wacom tablet.  Can't remember if it was a UC-LOGIC tablet though.  See if I can find that thread.

---

### Post by unused_bagels on 2011-08-29
Bus 002 Device 003: ID 046d:08af Logitech, Inc. QuickCam Easy/Cool
Bus 002 Device 002: ID 5543:0005 UC-Logic Technology Corp. Genius MousePen 8x6 Tablet
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

