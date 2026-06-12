---
title: "Acecad USB Tablet with bad karma in Karmic"
date: 2009-11-18
forum: General Help
---

### Post by RavanH on 2009-11-18
Hi,

I wanted to use an old Dynalink FreeDraw tablet with stylus and I remember it working in Gutsy (or before?). Now, with a fresh install of Karmic, when I plug in the tablet it does get recognized and I am able to control the mouse position with it but no clicking let alone drawing with pressure sensitivity in Gimp for instance :(

I notice xinput --list (see below) shows "Acecad USB Tablet" but with "Type is TOUCHPAD". That used to be "Type is TABLET"...

Is there any way to make Karmic use the tablet (with usb_acecad driver) as a tablet and not as a touchpad?

Thanks for any tips!

```

~$ xinput --list
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
"SynPS/2 Synaptics TouchPad"	id=2	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1
"Acecad USB Tablet"	id=3	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 5
	Num_axes is 3
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 5000
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 3750
		Resolution is 10000
	Axis 2 :
		Min_value is 0
		Max_value is 512
		Resolution is 10000
"Power Button"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Sleep Button"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=7	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
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

```

```
~$ dmesg | grep usb
[    0.172669] usbcore: registered new interface driver usbfs
[    0.172689] usbcore: registered new interface driver hub
[    0.172721] usbcore: registered new device driver usb
[    0.690109] usb usb1: configuration #1 chosen from 1 choice
[    0.752085] usb usb2: configuration #1 chosen from 1 choice
[    0.812091] usb usb3: configuration #1 chosen from 1 choice
[    1.290219] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    1.537164] usb 2-1: configuration #1 chosen from 1 choice
[    1.547792] usbcore: registered new interface driver hiddev
[    1.547859] usbcore: registered new interface driver usbhid
[    1.547864] usbhid: v2.6:USB HID core driver
[   18.337987] input: Acecad USB Tablet as /devices/pci0000:00/0000:00:1c.0/usb2/2-1/2-1:1.0/input/input5
[   18.338089] usbcore: registered new interface driver usb_acecad
```

And related excerpt from /var/log/Xorg.0.log :
```
(II) config/hal: Adding input device Acecad USB Tablet
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Acecad USB Tablet: always reports core events
(**) Acecad USB Tablet: Device: "/dev/input/event5"
(II) Acecad USB Tablet: Found 3 mouse buttons
(II) Acecad USB Tablet: Found x and y absolute axes
(II) Acecad USB Tablet: Found absolute touchpad
(II) Acecad USB Tablet: Configuring as touchpad
(**) Acecad USB Tablet: YAxisMapping: buttons 4 and 5
(**) Acecad USB Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Acecad USB Tablet" (type: TOUCHPAD)
(**) Acecad USB Tablet: (accel) keeping acceleration scheme 1
(**) Acecad USB Tablet: (accel) filter chain progression: 2.00
(**) Acecad USB Tablet: (accel) filter stage 0: 20.00 ms
(**) Acecad USB Tablet: (accel) set acceleration profile 0
(II) Acecad USB Tablet: initialized for absolute axes.

```

---

### Post by Favux on 2009-11-18
Hi RavanH,

It may be doable.  It sounds like you've installed the Acecad USB Tablet driver.  Is that what it's called?  Is the usb kernel driver for the Acecad drivers called usb_acecad.ko?  Do you see it in:
```
lsmod
```
or
```
lsmod | grep usb_acecad
```
If so then you just need a .fdi to attach the Acecad X11 driver to the tablet.  Right now the evdev driver is grabbing it:
> (II) config/hal: Adding input device Acecad USB Tablet
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so

and configuring it as a touchpad.  We'd need to look at your lshal:
```
lshal>lshal.txt
```

---

### Post by RavanH on 2009-11-19
> **Favux said:**
> Hi RavanH,

It may be doable.  It sounds like you've installed the Acecad USB Tablet driver.  Is that what it's called?  Is the usb kernel driver for the Acecad drivers called usb_acecad.ko?  Do you see it in:
```
lsmod
```
or
```
lsmod | grep usb_acecad
```

No, lsmod | grep usb_acecad returns nothing... The funny thing is that dmesg reports:
```
[   18.337987] input: Acecad USB Tablet as /devices/pci0000:00/0000:00:1c.0/usb2/2-1/2-1:1.0/input/input5
[   18.338089] usbcore: registered new interface driver usb_acecad
```
So I suppose it is indeed the usb_acecad driver that is being used...

> **Favux said:**
> If so then you just need a .fdi to attach the Acecad X11 driver to the tablet.  Right now the evdev driver is grabbing it:

and configuring it as a touchpad.  We'd need to look at your lshal:
```
lshal>lshal.txt
```
So I found that this created a text file lshal.txt in my home folder (sorry, I am not an expert Linux user)... I'll try and find all related sections and paste them here. 

I really appreciate your help, thanks :)

---

### Post by Favux on 2009-11-19
Hi RavanH,

Right, the text file is what we want.  If you right click on it you can compress it with Create Archive.  Then using Managing Attachments you can attach it to your post.

---

### Post by RavanH on 2009-11-19
> **Favux said:**
> Hi RavanH,

Right, the text file is what we want.  If you right click on it you can compress it with Create Archive.  Then using Managing Attachments you can attach it to your post.

Haha, I never noticed that paper-clip before! See attached archive for complete file...

---

### Post by Favux on 2009-11-19
Hi RavanH,

Great!  OK, I'll look lshal over.  Do you happen to have the old xorg.conf where you set up the Acecad?  That would be very helpful.

And what did you do to install the driver(s)?

---

### Post by RavanH on 2009-11-19
> **Favux said:**
> Hi RavanH,

Great!  OK, I'll look lshal over.  Do you happen to have the old xorg.conf where you set up the Acecad?  That would be very helpful.

And what did you do to install the driver(s)?

No, sorry, I do not have that anymore. However, I have been testing with setting the tablet up by creating a xorg.conf in Karmic and using the acecad driver after installing xserver-xorg-input-acecad in Synaptic. It seems to work (it is recognized as a tablet and I can click and drag and even set it up in Gimp for pressure sensitiveness) but it feels jumpy and nervous. Also, then there are two devices configured: one using the usb_acecad driver and the other the acecad driver. I really would like to use the kernel/evdev/hal one if that could be made to work.

Here is what I tested with in xorg.conf:
```
Section "InputDevice"
    Identifier     "Acecad USB Tablet"
    Driver         "acecad"
    Option         "Device" "auto-dev"
EndSection

Section "ServerLayout"
    Identifier     "Simple Layout"
    InputDevice    "Acecad USB Tablet" "SendCoreEvents"
EndSection
```

---

### Post by Favux on 2009-11-19
Hi RavanH,

OK, return the xorg.conf to pristine Karmic fresh install condition.  Remove anything you added for Acecad (or comment (#) it out) including probably the "ServerLayout".

Let's try this and see where it gets us:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Acecad">
        <merge key="input.x11_driver" type="string">acecad</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```
Add the entire above contents to the .fdi file you create with:
```
gksudo gedit /etc/hal/fdi/policy/10-acecad.fdi
```
Save, Close, and reboot.

What other features do you have.  Buttons on the stylus?  Eraser on the stylus?  Buttons on the tablet?  etc.  And do you remember how you set them up in xorg.conf?

---

### Post by RavanH on 2009-11-19
> **Favux said:**
> Hi RavanH,

OK, return the xorg.conf to pristine Karmic fresh install condition.  Remove anything you added for Acecad (or comment (#) it out) including probably the "ServerLayout".

I already did that to revert to the automatic usb_acecad setup by hal. I had also removed the xserver-xorg-input-acecad package again, so that is probably why...
> **Favux said:**
> ```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Acecad">
        <merge key="input.x11_driver" type="string">acecad</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```
Add the entire above contents to the .fdi file you create with:
```
gksudo gedit /etc/hal/fdi/policy/10-acecad.fdi
```
Save, Close, and reboot.
...did not work straight away. After re-installing the acecad package, it did indeed give a result somewhat similar to the xorg.conf method. Only without use of one of the two buttons on the stylus. But with the nervousness and jumpy mousepointer handling. Is there a way to use the usb_acecad (kernel?) driver because I like the way that one seems to get me much more subtle control over the mouse pointer...

> **Favux said:**
> What other features do you have.  Buttons on the stylus?  Eraser on the stylus?  Buttons on the tablet?  etc.  And do you remember how you set them up in xorg.conf?
No buttons on the tablet but two buttons (plus a sensitive point of-course) on the stylus. And an eraser? Is that not just assigning eraser function to a button?

With the above content for 10-acecad.fdi, the stylus works and the tip corresponds with left-mous-click. And the top button on the stylus corresponds with a right-mouse-click. I haven't tested pressure sensitivity in Gimp yet.

Have to go now but will be back within 24 hours to report further tests. Again, thanks for helping me out! :)

---

### Post by Favux on 2009-11-20
Hi RavanH,

Outstanding!  It sounds like the .fdi worked.  You're right, xserver-xorg-input-acecad needs to be installed.  I'm assuming you tried the tablet after installing that and the stylus didn't work.  In other words the package didn't install an acecad.fdi.  Otherwise having two .fdi's might be a problem.

We probably should look at:
```
xinput --list
```
and
```
Xorg.0.log
```
and also
```
lshal>lshal2.txt
```
> But with the nervousness and jumpy mousepointer handling.
That could be due to a low battery.  Does the stylus take a battery?  It could be a bad usb cable.  Also make sure it's firmly plugged in on both ends.  It could be a bad usb port on the computer end.  Also plug it in direct, not through a hub, while you're setting up.

Some drivers let you change the surpress level on the data the stylus is reporting, which could smooth it out.  Is there a manual for acecad?:
```
man acecad
```
That would be helpful to look at.  We could also try one at a time and/or some combination of:
```
      <merge key="input.x11_options.USB" type="string">on</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
```
Which is why a man would be helpful.

Some styli like the Wacom ones have a eraser-like button on the back of the stylus.  It depresses into the barrel of the stylus and also gives pressure in Gimp so you can smudge.

The stylus buttons depend on the driver so we could try adding to the .fdi:
```
<merge key="input.x11_options.Button2" type="string">2</merge>
<merge key="input.x11_options.Button3" type="string">3</merge>
```

> Is there a way to use the usb_acecad (kernel?) driver because I like the way that one seems to get me much more subtle control over the mouse pointer...
I'm not sure what you're saying.  There must be one active since your tablet is active, presumably from the acecad package.  Does it show up in lsmod?  If not it could be directly in the kernel in the usb-hid part.  Did I miss something and you had a tablet specific kernel driver at one point?

---

### Post by RavanH on 2009-11-20
> **Favux said:**
> ...I'm assuming you tried the tablet after installing that and the stylus didn't work.  In other words the package didn't install an acecad.fdi.  Otherwise having two .fdi's might be a problem.
You are right, the acecad package only installs /usr/lib/xorg/modules/input/acecad_drv.so (apart from some basic man, doc and bug additions) but even without the xserver-xorg-input-acecad package, the tablet is recognized as an Acecad USB Tablet and mouse pointer responds to stylus movement. As **dmesg** reports it is a driver called **usb_acecad** that is being used but strangely it is not listed by **lsmod**. 

With this 'default' config (nothing in xorg.conf, no .fdi and no xserver-xorg-input-acecad package) the mouse pointer control is very pleasant. Hard to describe but I am comparing it to when using the **acecad** driver (with xserver-xorg-input-acecad installed and either defined in xorg.conf or 10-acecad.fdi) where the it is hard to make the mouse pointer stay on top of (for example) a "Close window" button to successfully click it.

> **Favux said:**
> That could be due to a low battery.  Does the stylus take a battery?  It could be a bad usb cable.  Also make sure it's firmly plugged in on both ends.  It could be a bad usb port on the computer end.  Also plug it in direct, not through a hub, while you're setting up.
The battery is fresh, cable is connected directly to the laptop and works well (see above) when NOT using the acecad driver. But with the acecad driver, the mouse pointer control is much more difficult when aiming to click on a small screen object. 

So if it is not possible to adjust the default configuration (no xorg.conf, no .fdi no acecad driver) so that the tablet is used as a tablet and not as a touchpad (just as it is when using xorg.conf and acecad driver, see a previous post) and I am 'doomed' ;) to use the acecad driver then I hope some tinkering and fine-tuning will be possible... 

> **Favux said:**
> ...
Some drivers let you change the surpress level on the data the stylus is reporting, which could smooth it out.  Is there a manual for acecad?:
```
man acecad
```
That would be helpful to look at.  We could also try one at a time and/or some combination of:
```
      <merge key="input.x11_options.USB" type="string">on</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
```
Which is why a man would be helpful.
The info in man acecad is very minimal. See [http://linux.die.net/man/4/acecad](http://linux.die.net/man/4/acecad) . It states there are options possible but no options are described (just a text that the man page is incomplete). 

I will try some options as you describe to see what effect they have. 

> **Favux said:**
> ...
Some styli like the Wacom ones have a eraser-like button on the back of the stylus.  It depresses into the barrel of the stylus and also gives pressure in Gimp so you can smudge.

The stylus buttons depend on the driver so we could try adding to the .fdi:
```
<merge key="input.x11_options.Button2" type="string">2</merge>
<merge key="input.x11_options.Button3" type="string">3</merge>
```
Ok, so that is an eraser. The stylus in this tablet has nothing like that...

> **Favux said:**
> ...
I'm not sure what you're saying.  There must be one active since your tablet is active, presumably from the acecad package.  Does it show up in lsmod?  If not it could be directly in the kernel in the usb-hid part.  Did I miss something and you had a tablet specific kernel driver at one point?

You are not alone ;) I do not understand it either. Like I described: without any xorg.conf or .fdi not even xserver-xorg-input-acecad installed, the tablet is recognized and dmesg reports it using driver **usb_acecad** but lsmod does not list any driver like that... Weird.

When using this mysterious usb_acecad driver, xinput --list reports the tablet being used as "Type is TOUCHPAD". ```
"Acecad USB Tablet"	id=2	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 5
	Num_axes is 3
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 5000
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 3750
		Resolution is 10000
	Axis 2 :
		Min_value is 0
		Max_value is 512
		Resolution is 10000

```
When using the xserver-xorg-input-acecad package driver (acecad) xinput --list reports the tablet being used as "Type is TABLET". ```
"Acecad USB Tablet"	id=3	[XExtensionPointer]
	Type is TABLET
	Num_buttons is 3
	Num_axes is 3
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1024
		Resolution is 1000
	Axis 1 :
		Min_value is 0
		Max_value is 768
		Resolution is 1000
	Axis 2 :
		Min_value is 0
		Max_value is 512
		Resolution is 1000

```

Another weird thing with that usb_acecad driver, is that while the mouse pointer position can be controlled and none of the stylus buttons have a function, the tip of the stylus does have some sort of effect. I'll try to explain: I can move the mouse pointer by moving the stylus over the tablet without actually touching it (as it should be) but as soon as I touch the tablet with the tip of the stylus the mouse pointer will stop following stylus motion unless when the stylus moves WHILE the tip is pressed down on the tablet. Then when I lift the stylus away from the tablet and move it back close to it, the mouse pointer will follow stylus movement without touching the tablet again... 

It seems a bit weird behavior but actually makes the control of the mouse pointer more stable. When I want the pointer to stay above a very small area on the screen, I can just make it stay there by a short press with the tip after which I can easily press one of the buttons on the stylus with my thumb without making the pointer move away from its position! This last part is important to avoid mis-clicks (if you understand what I am trying to say)... This seems actually very useful where it not that none of the buttons have any effect :(

---

### Post by RavanH on 2009-11-20
It is getting complicated but to respond to your questions about the output of xinput, xorg.0.log and lshal, I would like to compare the basic fresh Karmic pristene no xorg.conf / no xserver-xorg-input-acecad (I'll call it EVDEV) setup with the setup where xserver-xorg-input-acecad module driver in combination with your .fdi is used (i'll call it ACECAD).

**EVDEV**
This setup gives nice mouse pointer control but stylus buttons have no function and I cannot click anything. Is that caused by "Type is TOUCHPAD"?

**Xorg.0.log ( EVDEV )**
```
(II) config/hal: Adding input device Acecad USB Tablet
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Acecad USB Tablet: always reports core events
(**) Acecad USB Tablet: Device: "/dev/input/event5"
(II) Acecad USB Tablet: Found 3 mouse buttons
(II) Acecad USB Tablet: Found x and y absolute axes
(II) Acecad USB Tablet: Found absolute touchpad
(II) Acecad USB Tablet: Configuring as touchpad
(**) Acecad USB Tablet: YAxisMapping: buttons 4 and 5
(**) Acecad USB Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Acecad USB Tablet" (type: TOUCHPAD)
(**) Acecad USB Tablet: (accel) keeping acceleration scheme 1
(**) Acecad USB Tablet: (accel) filter chain progression: 2.00
(**) Acecad USB Tablet: (accel) filter stage 0: 20.00 ms
(**) Acecad USB Tablet: (accel) set acceleration profile 0
(II) Acecad USB Tablet: initialized for absolute axes.
```

**Xinput --list ( EVDEV )**
```
"Acecad USB Tablet"	id=3	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 5
	Num_axes is 3
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 5000
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 3750
		Resolution is 10000
	Axis 2 :
		Min_value is 0
		Max_value is 512
		Resolution is 10000
```

**ACECAD**
This setup works but the mouse control is difficult especially right-clicking goes regularly wrong because of mouse movement while pressing the stylus button... Feels jumpy.

**Xorg.0.log ( ACECAD )**
```
(II) config/hal: Adding input device Acecad USB Tablet
(II) LoadModule: "acecad"
(II) Loading /usr/lib/xorg/modules/input//acecad_drv.so
(II) Module acecad: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Option "Device" "/dev/input/event5"
(--) ACECAD Tablet MaxX:5000 MaxY:3750 MaxZ:512
(==) Acecad USB Tablet is in absolute mode
(**) Acecad USB Tablet: always reports core events
(II) XINPUT: Adding extended input device "Acecad USB Tablet" (type: TABLET)
(II) Acecad USB Tablet Increment: 4
```

**Xinput --list ( ACECAD )**
```
"Acecad USB Tablet"	id=3	[XExtensionPointer]
	Type is TABLET
	Num_buttons is 3
	Num_axes is 3
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1024
		Resolution is 1000
	Axis 1 :
		Min_value is 0
		Max_value is 768
		Resolution is 1000
	Axis 2 :
		Min_value is 0
		Max_value is 512
		Resolution is 1000
```

Attached is the lshal2.txt which resulted from lshal when 10-acecad.fdi had the (minimal?) content ```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Acecad">
        <merge key="input.x11_driver" type="string">acecad</merge>
        <merge key="input.x11_options.Type" type="string">tablet</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

---

### Post by Favux on 2009-11-20
Hi RavanH,

Do not use:
```
        <merge key="input.x11_options.Type" type="string">tablet</merge>

```
You're not telling X you have a sylus.  Use:
```
        <merge key="input.x11_options.Type" type="string">stylus</merge>
```
Or better yet:
```
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>

```
That way applications like Blender that need to see "stylus" will work.

My guess is usb_acecad is associated with evdev.  Either in the kernel or with evdev.  You can see the evdev driver potentially has some options that it maybe possible to set:
```
(**) Acecad USB Tablet: (accel) keeping acceleration scheme 1
(**) Acecad USB Tablet: (accel) filter chain progression: 2.00
(**) Acecad USB Tablet: (accel) filter stage 0: 20.00 ms
(**) Acecad USB Tablet: (accel) set acceleration profile 0

```
You'd have to figure out which touchpad(?) .fdi it is setting your tablet up on by default and try to modify it.  You might be able to add stylus buttons.

So the acecad driver is a Xorg driver.  It's really what you should be using.  You could find out which Xorg dev.s are responsible for it and contact them directly.
> This setup works but the mouse control is difficult especially right-clicking goes regularly wrong because of mouse movement while pressing the stylus button... Feels jumpy.
That just might need the addition of:
```
        <merge key="input.x11_options.TPCButton" type="string">off</merge>

```
or "on".  Depending on what the acecad driver supports some of the options on this [page]("http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom") of the LinuxWacomProject's HOWTO may also apply when translated into .fdi lines.

---

### Post by RavanH on 2009-11-22
> **Favux said:**
> Hi RavanH,

Do not use:
```
        <merge key="input.x11_options.Type" type="string">tablet</merge>

```
You're not telling X you have a sylus.  Use:
```
        <merge key="input.x11_options.Type" type="string">stylus</merge>
```
Or better yet:
```
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>

```
That way applications like Blender that need to see "stylus" will work.
Funny, even the minimalistic content of ```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Acecad">
        <merge key="input.x11_driver" type="string">acecad</merge>
      </match>
    </match>
  </device>
</deviceinfo>
``` works just the same as anything else... I have also noticed that whatever I try in the 10-acecad.fdi, only the top half of the tablet is used. Any possibilities of forcing it to use the complete tablet pad space?

> **Favux said:**
> 
My guess is usb_acecad is associated with evdev.  Either in the kernel or with evdev.  You can see the evdev driver potentially has some options that it maybe possible to set:
```
(**) Acecad USB Tablet: (accel) keeping acceleration scheme 1
(**) Acecad USB Tablet: (accel) filter chain progression: 2.00
(**) Acecad USB Tablet: (accel) filter stage 0: 20.00 ms
(**) Acecad USB Tablet: (accel) set acceleration profile 0

```
You'd have to figure out which touchpad(?) .fdi it is setting your tablet up on by default and try to modify it.  You might be able to add stylus buttons.
Hmmm, sounds complicated and way over my head... I'll pursue the acecad driver approach as you suggest then :) Unless that one cannot be forced to use the complete tablet (like the evdev driver does) instead of just the top half!

> **Favux said:**
> 
So the acecad driver is a Xorg driver.  It's really what you should be using.  You could find out which Xorg dev.s are responsible for it and contact them directly.

That just might need the addition of:
```
        <merge key="input.x11_options.TPCButton" type="string">off</merge>

```
or "on".  Depending on what the acecad driver supports some of the options on this [page]("http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom") of the LinuxWacomProject's HOWTO may also apply when translated into .fdi lines.

I'll continue tinkering with options and let you know if I find any useful settings... 

Thanks again for your support, Favux! I see you are quite active on tablet related threads. Much appreciated :)

---

### Post by Favux on 2009-11-22
Hi RavanH,

It's possible the acecad driver doesn't auto calibrate.
> Funny, even the minimalistic content of... works just the same as anything else... I have also noticed that whatever I try in the 10-acecad.fdi, only the top half of the tablet is used. Any possibilities of forcing it to use the complete tablet pad space?

That suggests the driver isn't attaching.  Look in Xorg.0.log and see what's happening.  With luck it will have the coordinates you need to and you can add them manually to the .fdi something like:
```
		<merge key="input.x11_options.BottomY" type="string">3909</merge>
		<merge key="input.x11_options.BottomX" type="string">3947</merge>
		<merge key="input.x11_options.TopY" type="string">185</merge>
		<merge key="input.x11_options.TopX" type="string">186</merge>

```
if the driver really won't calibrate the tablet.

---

### Post by RavanH on 2009-11-23
> **Favux said:**
> Hi RavanH,

It's possible the acecad driver doesn't auto calibrate.

That suggests the driver isn't attaching.  Look in Xorg.0.log and see what's happening.  With luck it will have the coordinates you need to and you can add them manually to the .fdi something like:
```
		<merge key="input.x11_options.BottomY" type="string">3909</merge>
		<merge key="input.x11_options.BottomX" type="string">3947</merge>
		<merge key="input.x11_options.TopY" type="string">185</merge>
		<merge key="input.x11_options.TopX" type="

```
if the driver really won't calibrate the tablet.

Ok, I found ```
(--) ACECAD Tablet MaxX:5000 MaxY:3750 MaxZ:512

``` in xorg.0.log so I tried in 10-acecad.fdi ```
	<merge key="input.x11_options.Mode" type="string">absolute</merge>
	<merge key="input.x11_options.TopX" type="string">0</merge>
	<merge key="input.x11_options.BottomX" type="string">5000</merge>
	<merge key="input.x11_options.TopY" type="string">0</merge>
	<merge key="input.x11_options.BottomY" type="string">3750</merge>

```
Sadly, that did not change anything...

I had noticed that in the GDM login screen --before logging in-- the complete tablet surface is used for mouse movement but as soon as I had logged in, only half the surface is used. It turns out that the driver (or X?) auto calibrates the tablet correctly when I am using only one screen (or more but mirrored) but as soon as I set up my second screen to extend the desktop (doubling it verticaly) the tablet surface is halved... This happens on the fly.

No idea how to prevent this :(

---

### Post by Favux on 2009-11-23
Hi RavanH,

Good, finding coordinates in Xorg.0.log should help.  So what we know now is:
```
        <merge key="input.x11_options.TopX" type="string">???</merge>
        <merge key="input.x11_options.TopY" type="string">???</merge>
        <merge key="input.x11_options.BottomX" type="string">???</merge>
        <merge key="input.x11_options.BottomY" type="string">???</merge>
        <merge key=”input.x11_options.MaxX” type=”string”>5000</merge>
        <merge key=”input.x11_options.MaxY” type=”string”>3750</merge>
        <merge key="input.x11_options.zMin" type="string">0</merge>
        <merge key="input.x11_options.zMax" type="string">511</merge>
```
Presumably TopX and Y are somewhere near zero.  From your "xinput --list"'s when it using the Acecad drivers and it is called a "Type is TABLET" the Bottom X and Y are 1024 and 768 (or the reverse).  But that sounds suspiciously like a screen resolution.

So just add what we know:
```
        <merge key=”input.x11_options.MaxX” type=”string”>5000</merge>
        <merge key=”input.x11_options.MaxY” type=”string”>3750</merge>
        <merge key="input.x11_options.zMin" type="string">0</merge>
        <merge key="input.x11_options.zMax" type="string">511</merge>
```
And see where that gets us.  Then you can try manually adding the rest, if needed, and changing the values until they "fit".

The dual screen thing probably depends on what the driver supports and what video you have.  What's your video chipset?  I'd keep it to one screen for now until we've got the tablet sorted out.

---

### Post by RavanH on 2009-11-23
> **Favux said:**
> ...The dual screen thing probably depends on what the driver supports and what video you have.  What's your video chipset?  I'd keep it to one screen for now until we've got the tablet sorted out.
It is a ATI Radeon Xpress 200M chipset ( Ouch! I have had trouble with it from the start until fglrx became stable, but now that support for this chipset is dropped in fglrx I returned to the open radeon driver... )

The thing is: the acecad driver seems to be pretty OK when using only one screen (or two mirrored) and after some testing with a freshly created account (and mirrored screen layout) does not seem to need any tweaking at all even with the most basic .fdi content :)

So I guess the "jumpiness" is caused by this two screen setup bug: While by positioning the external screen (1024x768 LCD) above the laptop screen (1280x800 LCD) my desktop height has grown from 800px to 1568px, on the other hand the active drawing area on my tablet has been halved! This obviously results in nearly 4 times increase in vertical sensitivity of pen movement.

The double screen layout needed a virtual display size set up in Xorg.conf: ```
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	2048 2048
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
``` Would that give us something to work with?

I really hope the full tablet area can be restored while keeping the double screen layout because the trade-off is not appealing to me.

---

### Post by RavanH on 2009-11-24
Hi Favux,

this multi-monitor thing is a beast. Even with the second monitor switched off in Screen config, the acecad decides to adjust the work-area on the tablet to fit the smallest monitors ratio (3:4). Only after completely disconnecting it, the driver will use the complete tablet area.

To get any grip on this behaviour, I have been testing my head off.

> **Favux said:**
> ...So just add what we know:
```
        <merge key=&#8221;input.x11_options.MaxX&#8221; type=&#8221;string&#8221;>5000</merge>
        <merge key=&#8221;input.x11_options.MaxY&#8221; type=&#8221;string&#8221;>3750</merge>
        <merge key="input.x11_options.zMin" type="string">0</merge>
        <merge key="input.x11_options.zMax" type="string">511</merge>
```
And see where that gets us.  Then you can try manually adding the rest, if needed, and changing the values until they "fit"...

Tried that, changed values... nothing.

Tried any other X/Y related parameter I could find... nothing.

Also tried various parameters from the wacom how-to on [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom) like 
```
<merge key="input.x11_options.mmonitor" type="string">off</merge>
``` and ```
<merge key="input.x11_options.TwinView" type="string">vertical</merge>
``` to get the acecad driver to either ignore or recognize my double monitor setup... nothing. 

I found a man page on the SVN of acecad on sourceforge ( [https://svn.sourceforge.net/svnroot/acecad/acecad-xinput/acecad.man](https://svn.sourceforge.net/svnroot/acecad/acecad-xinput/acecad.man) ) and tried **every** parameter that is described there but without **any** effect!

The acecad driver does not seem to listen to anything. Not even ```
<merge key="input.x11_options.Mode" type="string">Relative</merge>
``` and even though Xorg.0.log reports ```
(**) stylus is in relative mode
``` the stylus still behaves as in absolute mode :(

No parameter has any effect. Absolutely NOTHING! :mad:

I decided to test some with the evdev driver and removed the line ```
<merge key="input.x11_driver" type="string">acecad</merge>
``` Immediately (after restarting X), the stylus went to relative mode and (thus?) the complete tablet area was usable even when I have two monitors connected. Somehow, I end up liking the evdev driver much better. If only it would accept/relay clicks and pressure...

**Xorg.0.log** and **xinput --list** now both report the stylus as "stylus" and not "Acecad USB Tablet" like they would *without* the 10-acecad.fdi so the line ```
<merge key="info.product" type="string">stylus</merge>
``` works even without loading the acecad driver! Sadly, the line ```
<merge key="input.x11_options.Type" type="string">stylus</merge>
``` does nothing. Xinput --list reports ```
"stylus"	id=2	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 5
	Num_axes is 3
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 5000
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 3750
		Resolution is 10000
	Axis 2 :
		Min_value is 0
		Max_value is 512
		Resolution is 10000

``` (Note TOUCHPAD there instead of TABLET... Also note the "Mode is Absolute" in there, while the tablet behaves in relative mode!?)

I hope it is possible to use that file to further tweak the usb_acecad / evdev driver to accept stylus tip and buttons. But I have NO idea how... I cannot find anything via Google except *this* thread!

Any ideas?

---

### Post by Favux on 2009-11-24
Hi RavanH,

I suppose you could try:
```
<merge key="input.x11_options.Button1" type="string">1</merge>
<merge key="input.x11_options.Button2" type="string">2</merge>
<merge key="input.x11_options.Button3" type="string">3</merge>
```
And you could take a look at this [post]("http://ubuntuforums.org/showpost.php?p=7727817&postcount=70").

---

### Post by RavanH on 2009-11-24
> **Favux said:**
> Hi RavanH,

I suppose you could try:
```
<merge key="input.x11_options.Button1" type="string">1</merge>
<merge key="input.x11_options.Button2" type="string">2</merge>
<merge key="input.x11_options.Button3" type="string">3</merge>
```
And you could take a look at this [post]("http://ubuntuforums.org/showpost.php?p=7727817&postcount=70").
Hi Favux, that also does not change a thing... With or without it:
```
~$ xinput get-button-map "stylus"
1 2 3 4 5

```
So aparently, there are more than 3 buttons configured while the stylus has only 3. Maybe only mapped buttons 4 and 5 are assigned to clicks? Since X seems to be thinking it is a Touchpad, those might be left and richt click buttons? Is there any command to show me?
```
~$ xinput list-props "stylus"
Device 'stylus':
	Device Enabled (134):	1
	Evdev Reopen Attempts (267):	10
	Evdev Axis Inversion (268):	0, 0
	Evdev Axis Calibration (269):	
	Evdev Axes Swap (270):	0
	Evdev Middle Button Emulation (271):	2
	Evdev Middle Button Timeout (272):	50
	Evdev Wheel Emulation (273):	0
	Evdev Wheel Emulation Axes (274):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (275):	10
	Evdev Wheel Emulation Timeout (276):	200
	Evdev Wheel Emulation Button (277):	4
	Evdev Drag Lock Buttons (278):	0

```
Does this tell me what the 5 buttons are actually supposed to be doing?

---

### Post by Favux on 2009-11-24
Hi RavanH,

Button1 is suppose to be the stylus tip and by default set to 1 (left mouse click).  Sounds like the touchpad driver doesn't know what a stylus is.

I guess the 5 buttons would give you the capabaility of a "5 button mouse" touchpad if you could map them.

And it sounds like the Acecad driver may not be interfacing with Xinput correctly.  I'm pretty stuck at this point.

Here's a link to evdev:  [https://fedoraproject.org/wiki/Features/EvdevInputDriver](https://fedoraproject.org/wiki/Features/EvdevInputDriver)

---

### Post by RavanH on 2009-11-25
> **Favux said:**
> Hi RavanH,

Button1 is suppose to be the stylus tip and by default set to 1 (left mouse click).  Sounds like the touchpad driver doesn't know what a stylus is.

I guess the 5 buttons would give you the capabaility of a "5 button mouse" touchpad if you could map them.

And it sounds like the Acecad driver may not be interfacing with Xinput correctly.  I'm pretty stuck at this point.

Here's a link to evdev:  [https://fedoraproject.org/wiki/Features/EvdevInputDriver](https://fedoraproject.org/wiki/Features/EvdevInputDriver)

Well thank you Favux, for helping me along this far :) I'll continue with my quest and report back if I find a way to make it work... Would you happen to know where/how I could contact acecad driver devs? Or is that a dead project?

---

### Post by Favux on 2009-11-25
Hi RavanH,

> Would you happen to know where/how I could contact acecad driver devs?
Well somewhere on the [Xorg site]("http://www.x.org/wiki/") should be a link or information related to that.

Although come to think of it I think I tracked down the Trident dev.s through the Debian git or search site.

---

### Post by Magnes on 2009-12-15
[http://ubuntuforums.org/showthread.php?p=8504734#post8504734](http://ubuntuforums.org/showthread.php?p=8504734#post8504734) - this method works for me. It must be ACECAD, not Acecad in info.product.

---

### Post by RavanH on 2009-12-16
> **Magnes said:**
> [http://ubuntuforums.org/showthread.php?p=8504734#post8504734](http://ubuntuforums.org/showthread.php?p=8504734#post8504734) - this method works for me. It must be ACECAD, not Acecad in info.product.

I suppose that depends on what "dmesg | grep usb" reports after plugging the tablet in. In my case it is:
...
[   18.337987] input: Acecad USB Tablet as /devices/pci0000:00/0000:00:1c.0/usb2/2-1/2-1:1.0/input/input5
...

Here "Acecad" is used, not "ACECAD" and subsequently my 10-acecad.fdi is completely ignored when I use the latter in info.product.

---

