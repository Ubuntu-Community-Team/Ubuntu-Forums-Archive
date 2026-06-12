---
title: "xorg joystick key events"
date: 2010-03-17
forum: General Help
---

### Post by martron88 on 2010-03-17
I've been fooling around with a Dance Dance Revolution mat trying to get some of the arrows to send key events to the desktop.  Following [http://www.x.org/archive/X11R7.5/doc/man/man4/joystick.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/joystick.4.html) I edited my xorg.conf and have most of it working, except the key commands.  The best I can get is each button outputs a number whenever it's pressed (the down-left arrow for instance outputs a 1) and I can map a button to turn it on and off.

The relevant section of xorg.conf:

```
Section "InputDevice"
	Identifier "DDRMat"
	Driver "joystick"
	Option "Device"   "/dev/input/js0"
	Option "Path"   "/dev/input/js0"
	Option "StartMouseEnabled" "False"
	Option "Buttons" "10"

	Option "MapButton1" "key=b"
	Option "MapButton2" "key=c"
	Option "MapButton3" "key=d"
	Option "MapButton4" "key=0x0045"
	Option "MapButton5" "key=0x0046"
	Option "MapButton6" "key=0x0047"
	Option "MapButton7" "key=0x0048"
	Option "MapButton8" "key=0x0075"
	Option "MapButton9" "disable-keys"
	Option "MapButton10" "key=0x0070"

EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice     "DDRMat"     "SendCoreEvents"
EndSection
```

Note that I've tried a few methods of assigning keys.  None have gotten me too far.  Option "StartMouseEnabled" "False" is in there to keep the mat from controlling the mouse.

Thoughts anyone?

---

### Post by mcoleman44 on 2010-03-17
Im not really an expert at this, but this might help you see what events control the device.
```
sudo xxd /dev/input/eventX

```

Just try all the events and see which events give you a response when using the joystick.
ctrl+c to exit the application.

---

### Post by martron88 on 2010-03-17
> **mcoleman44 said:**
> Im not really an expert at this, but this might help you see what events control the device.
```
sudo xxd /dev/input/eventX

```

Just try all the events and see which events give you a response when using the joystick.
ctrl+c to exit the application.

I just tried it and all of the buttons generate some characters (which don't exactly mean much to me).

The main problem isn't whether the buttons generate events but rather that no matter what key code I try to map them to, they always end up printing the digits from 0-9.

---

### Post by mcoleman44 on 2010-03-17
Do me a favor and post the output of 
```
xinput --list
```

---

### Post by martron88 on 2010-03-17
> **mcoleman44 said:**
> Do me a favor and post the output of 
```
xinput --list
```

This'll be the relevant section:
```
"RedOctane RedOctane USB Pad (keys)"	id=17	[XExtensionKeyboard]
	Type is JOYSTICK
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"RedOctane RedOctane USB Pad"	id=16	[XExtensionPointer]
	Type is JOYSTICK
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1440
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is 900
		Resolution is 1

```

---

### Post by mcoleman44 on 2010-03-17
Well, thats a bummer. I was hoping each button was a different event/id. 
If it was we could have just reattached it.
something like 
```
xinput reattach 17 XX
```

Oh well. Im not sure what to tell you now.

---

### Post by martron88 on 2010-03-17
> **mcoleman44 said:**
> Well, thats a bummer. I was hoping each button was a different event/id. 
If it was we could have just reattached it.
something like 
```
xinput reattach 17 XX
```

Oh well. Im not sure what to tell you now.

It's cool, thanks for introducing me to some new commands.  I feel really close, I mean the disable-keys option works so somehow this should work in a predictable manner...

---

### Post by mcoleman44 on 2010-03-17
I think maybe another device is trying to grab the events and thats why your xorg isnt working. Take a look at your xorg.0.log and look for EE

---

### Post by martron88 on 2010-03-17
Found someone with the same problem (but no solution):
[http://www.mail-archive.com/xorg@lists.freedesktop.org/msg07136.html](http://www.mail-archive.com/xorg@lists.freedesktop.org/msg07136.html)

I ran xev and my buttons #1 and #3 correspond to the same keycodes as in that post.

---

### Post by martron88 on 2010-03-17
> **mcoleman44 said:**
> I think maybe another device is trying to grab the events and thats why your xorg isnt working. Take a look at your xorg.0.log and look for EE

The only potentially relevant EE is:
```
(EE) Logitech Logitech Illuminated Keyboard: failed to initialize for relative axes.
```

So far as I know, my keyboard does not have any axes.

---

### Post by martron88 on 2010-03-17
Interesting development and random solution.  By remapping button 1 to a button (overriding the default 1) and then mapping all buttons to the desired keycodes makes everything work properly.

I've also switched from using xorg.conf to hal for hotplug support.

To get this mat working as I wanted I had to do the following steps:

1) add to xorg.conf in the ServerFlags section
```
Option "AllowEmptyInput"	"True"
```

2) create the file /etc/hal/fdi/policy/x11-joystick.fdi and paste the following:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input">
      <!-- Match on anything you like from lshal -->
      <match key="input.product" string_outof="RedOctane RedOctane USB Pad">
        
        <merge key="input.x11_driver" type="string">joystick</merge>
        
        <!-- Arbitrary options can be passed to the driver using 
             the input.x11_options property since xorg-server-1.5. -->

        <!-- DEFAULT CONFIGURATION 
             Change this to override the default settings of the input driver.
        -->

	<merge key="input.x11_options.StartMouseEnabled" type="string">False</merge>
	<merge key="input.x11_options.StartKeysEnabled" type="string">False</merge>
	<merge key="input.x11_options.MapButton1" type="string">button=15</merge>	

	<merge key="input.x11_options.MapButton1" type="string">key=a,z</merge>
        <merge key="input.x11_options.MapButton2" type="string">key=b</merge>
        <merge key="input.x11_options.MapButton3" type="string">key=c</merge>
        <merge key="input.x11_options.MapButton4" type="string">key=d</merge>
        <merge key="input.x11_options.MapButton5" type="string">key=e</merge>
        <merge key="input.x11_options.MapButton6" type="string">key=f</merge>
        <merge key="input.x11_options.MapButton7" type="string">key=g</merge>
        <merge key="input.x11_options.MapButton8" type="string">key=h</merge>
        <merge key="input.x11_options.MapButton9" type="string">disable-keys</merge>
        <merge key="input.x11_options.MapButton10" type="string">key=j</merge>

<!--
        <merge key="input.x11_options.MapAxis1" type="string">mode=relative axis=+1x deadzone=5000</merge>
        <merge key="input.x11_options.MapAxis2" type="string">mode=relative axis=+1y deadzone=5000</merge>
        <merge key="input.x11_options.MapAxis3" type="string">mode=relative axis=+1zx deadzone=5000</merge>
        <merge key="input.x11_options.MapAxis4" type="string">mode=relative axis=+1zy deadzone=5000</merge>
        <merge key="input.x11_options.MapAxis5" type="string">mode=accelerated axis=+1x deadzone=5000</merge>
        <merge key="input.x11_options.MapAxis6" type="string">mode=accelerated axis=+1y deadzone=5000</merge>
-->
        <!-- EXAMPLES
        <merge key="input.x11_options.DebugLevel" type="string">5</merge>
        <merge key="input.x11_options.AutoRepeat" type="string">500 4</merge>
        <merge key="input.x11_options.MapButton4" type="string">key=Alt_L+Tab</merge>
        <merge key="input.x11_options.MapButton8" type="string">amplify=0.3</merge>
        <merge key="input.x11_options.MapButton9" type="string">disable-mouse</merge>
        <merge key="input.x11_options.MapButton10" type="string">key=space</merge>

        <merge key="input.x11_options.MapAxis1" type="string">mode=accelerated keylow=Left keyhigh=Right</merge>
        <merge key="input.x11_options.MapAxis2" type="string">mode=accelerated keylow=Up keyhigh=Down</merge>
        -->
      </match>
    </match>
  </device>
</deviceinfo>
```

3) restart hal
```
sudo /etc/init.d/hal restart
```

4) restart xserver (ctrl-alt-backspace if dontzap is disabled).

If you make changes to the configuration file (after having restarted hal and xserver once) all you should need to do is unplug and replug the usb cable to the joystick to use the changes.

Note that the configuration I provided disables key presses by default, which I can turn on by pressing button9.  If you want them on by default then change
```
<merge key="input.x11_options.StartMouseEnabled" type="string">False</merge>
```
to True.

Many more configuration parameters can be found at:
[http://www.x.org/archive/X11R7.5/doc/man/man4/joystick.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/joystick.4.html)

And to be clear, what made the keys all work properly for me was to add the line
```
<merge key="input.x11_options.MapButton1" type="string">button=15</merge>	
```
before defining the key codes.  I don't have any good explanation as to why it works. Maybe it fools evdev into using the joystick driver properly?

---

### Post by martron88 on 2010-03-17
Now the fun part.  Since I'm standing on a dance mat while using the computer (writing papers/code/internetting), what keys should I map the buttons to?

Some ideas to get the ball rolling:
[LIST]
[*]Multimedia keys (play/next song/prev song/mute)
[*]Copy/paste
[*]Switch desktop (I have 4 desktops in a square configuration)
[/LIST]

---

