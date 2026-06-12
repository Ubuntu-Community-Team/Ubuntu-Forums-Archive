---
title: "eGalaxy touch screen"
date: 2010-05-15
forum: General Help
---

### Post by mailinatorjack on 2010-05-15
Hi all, I'm running Lucid Lynx with latest updates. I have an eGalaxy touch screen as can be seen from lsusb:
```

Bus 003 Device 008t: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen

```

Basically my current status is that the touch screen "works" but I can't calibrate it. I'm going to take a step back though because it seems to be part of a bigger problem. 

First of all, when I run calibrate, an error is returned saying that it can't find the evtouch device. This is because evtouch doesn't load properly within X. Here is the relevant X log:
```

(II) config/udev: Adding input device &#1033; &#1033; (/dev/input/event4)
(**) &#1033; &#1033;: Applying InputClass "evdev touchscreen catchall"
(**) &#1033; &#1033;: Applying InputClass "touchscreen catchall"
(II) LoadModule: "evtouch"
(II) Loading /usr/lib/xorg/modules/input/evtouch_drv.so
(II) Module evtouch: vendor="Kenan Esau"
        compiled for 1.7.6, module version = 0.8.8
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 7.0
State: S_UNTOUCHED      Action: No Action               Button: 0
State: S_TOUCHED        Action: No Action               Button: 0
State: S_LONGTOUCHED    Action: down            Button: 1
State: S_MOVING Action: No Action               Button: 0
State: S_MAYBETAPPED    Action: click           Button: 1
State: S_ONEANDAHALFTAP Action: down            Button: 3
(**) EVTouch TouchScreen: always reports core events
(II) XINPUT: Adding extended input device "EVTouch TouchScreen" (type: TOUCHSCREEN)
(**) Option "Device" "/dev/input/event4"
(II) EVTouch TouchScreen: Found absolute axes
(II) config/udev: Adding input device &#1033; &#1033; (/dev/input/mouse1)
(**) &#1033; &#1033;: Applying InputClass "touchscreen catchall"
State: S_UNTOUCHED      Action: No Action               Button: 0
State: S_TOUCHED        Action: No Action               Button: 0
State: S_LONGTOUCHED    Action: down            Button: 1
State: S_MOVING Action: No Action               Button: 0
State: S_MAYBETAPPED    Action: click           Button: 1
State: S_ONEANDAHALFTAP Action: down            Button: 3
(**) EVTouch TouchScreen: always reports core events
(II) XINPUT: Adding extended input device "EVTouch TouchScreen" (type: TO(**) Option "Device" "/dev/input/mouse1"
(EE) ioctl EVIOCGNAME failed: Inappropriate ioctl for device
Unable to query/initialize EVTouch hardware.
[dix] couldn't enable device 9
(EE) Couldn't init device "&#1033; &#1033;"
(II) UnloadModule: "evtouch"

```

And there lies my issue. Relevant output of /proc/bus/input/devices:
```

I: Bus=0003 Vendor=0eef Product=0001 Version=0100
N: Name="&#1033; &#1033;"
P: Phys=usb-0000:00:04.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:04.0/usb3/3-2/3-2:1.0/input/input6
U: Uniq=
H: Handlers=mouse1 event4 
B: EV=b
B: KEY=400 0 0 0 0 0 0 0 0 0 0
B: ABS=3

```

Some other background information; I read that someone else has got this screen working with Lucid Lynx out of the box. However, this wasn't the case with me. It was completely unresponsive. I realised that it was using the usbhid kernel module. When I removed this and did a modprobe usbtouchscreen, the screen came to life instantly, however I couldn't calibrate it, as it couldn't find evtouch.

So, does anybody have any ideas as to what the issue could be here? It's weird how the touch screen is responsive even without loading evtouch X module, but I guess it's needed for correct calibration.

Any help greatly appreciated!

---

### Post by mailinatorjack on 2010-05-16
Hello, just an update here.

I've got rid of the error in X. What I did was removed /usr/lib/X11/xorg.conf.d/10-evtouch.conf. Here is my relevant log now:

```

(II) config/udev: Adding input device &#1033; &#1033; (/dev/input/event4)
(**) &#1033; &#1033;: Applying InputClass "evdev touchscreen catchall"
(**) &#1033; &#1033;: always reports core events
(**) &#1033; &#1033;: Device: "/dev/input/event4"
(II) &#1033; &#1033;: Found absolute axes
(II) &#1033; &#1033;: Found x and y absolute axes
(II) &#1033; &#1033;: Found absolute touchscreen
(II) &#1033; &#1033;: Configuring as touchscreen
(**) &#1033; &#1033;: YAxisMapping: buttons 4 and 5
(**) &#1033; &#1033;: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "&#1033; &#1033;" (type: TOUCHSCREEN)
(II) &#1033; &#1033;: initialized for absolute axes.
(II) config/udev: Adding input device &#1033; &#1033; (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)

```

Now when I run xinput_calibrator_x11 --device 9 -v:

```

DEBUG: XInputExtension version is 2.0
DEBUG: Skipping virtual master devices and devices without axis valuators.
DEBUG: Selected device: &#1033; &#1033;
DEBUG: Not usbtouchscreen calibrator: Not a usbtouchscreen device
DEBUG: Evdev Axis Calibration not set, setting to axis valuators to be sure.
DEBUG: Succesfully applied axis calibration.
DEBUG: Read axes swap value of 0.
Calibrating EVDEV driver for "&#1033; &#1033;" id=9
        current calibration values (from XInput): min_x=0, max_x=2047 and min_y=0, max_y=2047
DEBUG: Adding click 0 (X=306, Y=0)
DEBUG: Adding click 1 (X=1023, Y=0)
DEBUG: Adding click 2 (X=311, Y=474)
DEBUG: Adding click 3 (X=1023, Y=485)

Doing dynamic recalibration:
        Setting new calibration data: 378, 2283, -213, 1491
DEBUG: Succesfully applied axis calibration.

```

Strange how it says "Not usbtouchscreen calibrator: Not a usbtouchscreen device" however it now tries to calibrate it. It says it dynamically calibrated it successfully, but it's basically still the same as it was before, touches are completely inaccurate. Putting the calibration details into xorg.conf makes no difference either.

It's not ignoring my X options, because I can reverse Y axis which does take affect. 

It would be interesting to see what driver other Lucid Lynx users are using for their device. If you type this: 
```

usb-devices

```

you will see some lines regarding your unit. Here is mine:
```

T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0eef ProdID=0001 Rev=01.00
S:  Manufacturer=&#1033;
S:  Product=&#1033;
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=44mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbtouchscreen

```

The "Driver=usbtouchscreen" says I'm using usbtouchscreen driver. By default, it would use usbhid however nowhere have I heard of anyone actually changing this driver from default usbhid to usbtouchscreen. I had to, otherwise by device would not show up when I cat /proc/bus/input/devices. 

Thanks again for any help!

---

### Post by mailinatorjack on 2010-05-21
Hi everyone, I managed to fix my problem, pretty much. For anybody else out there with the same issue, the key is to not install the evtouch driver (ie don't install xserver-xorg-input-evtouch). Make sure that usbhid is loaded *after* usbtouchscreen.

You will then (at least I did anyway) have a functional touch screen with the Y axis swapped. Run the calibration tool xinput_calibrator_x11 which is available from [http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator) - install dev tools so you can compile it.

Run xinput_calibrator_x11 --list to list devices. The penny that dropped for me is by running xinput test <device>. All along I had thought I was using the correct device but I wasn't. Run xinput test and then move finger over the screen and you'll get output. For me, the evtouch driver was being used which was causing issues, so remove it.

One thing I haven't managed to do is create correct udev rules. I don't really care about that as I boot straight into X without login so I just run a startup script that sets calibration through xinput (the xinput_calibrator_x11 tool will tell you how to do it after you calibrate).

---

