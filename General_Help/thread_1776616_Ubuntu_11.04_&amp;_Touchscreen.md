---
title: "Ubuntu 11.04 &amp; Touchscreen"
date: 2011-06-06
forum: General Help
---

### Post by mr-rob on 2011-06-06
Hello,
How do i correct my touchscreen being picked up and working like a touchpad?
 
xorg.0.log
13.266] (II) config/udev: Adding input device IDEACOM IDC 6650 (/dev/input/mouse0)
[ 13.266] (II) No input driver/identifier specified (ignoring)
[ 13.266] (II) config/udev: Adding input device IDEACOM IDC 6650 (/dev/input/event4)
[ 13.266] (**) IDEACOM IDC 6650: Applying InputClass "touchpad catchall"
[ 13.266] (II) LoadModule: "synaptics"
[ 13.266] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 13.426] (II) Module synaptics: vendor="X.Org Foundation"
[ 13.426] compiled for 1.10.0.902, module version = 1.3.99
[ 13.426] Module class: X.Org XInput Driver
[ 13.426] ABI class: X.Org XInput driver, version 12.3
[ 13.426] (II) Using input driver 'synaptics' for 'IDEACOM IDC 6650'
[ 13.426] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 13.426] (**) IDEACOM IDC 6650: always reports core events
[ 13.426] (**) Option "Device" "/dev/input/event4"
[ 13.570] (--) IDEACOM IDC 6650: x-axis range 0 - 8191
[ 13.570] (--) IDEACOM IDC 6650: y-axis range 0 - 8191
[ 13.570] (II) IDEACOM IDC 6650: device does not report pressure, will use touch data.
[ 13.570] (--) IDEACOM IDC 6650: buttons: left right
[ 13.570] (--) IDEACOM IDC 6650: invalid pressure range. defaulting to 0 - 256
[ 13.570] (--) IDEACOM IDC 6650: invalid finger width range. defaulting to 0 - 16
[ 13.570] (--) IDEACOM IDC 6650: touchpad found
[ 13.570] (**) IDEACOM IDC 6650: always reports core events
[ 13.572] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input4/event4"
[ 13.572] (II) XINPUT: Adding extended input device "IDEACOM IDC 6650" (type: TOUCHPAD)
[ 13.572] (**) IDEACOM IDC 6650: (accel) MinSpeed is now constant deceleration 2.5
[ 13.572] (**) IDEACOM IDC 6650: MaxSpeed is now 1.75
[ 13.572] (**) IDEACOM IDC 6650: AccelFactor is now 0.017
[ 13.572] (**) IDEACOM IDC 6650: (accel) keeping acceleration scheme 1
[ 13.572] (**) IDEACOM IDC 6650: (accel) acceleration profile 1
[ 13.572] (**) IDEACOM IDC 6650: (accel) acceleration factor: 2.000
[ 13.572] (**) IDEACOM IDC 6650: (accel) acceleration threshold: 4
[ 13.572] (II) IDEACOM IDC 6650: failed to open grail, no gesture support
[ 13.572] (--) IDEACOM IDC 6650: touchpad found
 
have tried this ubuntuforums.org/showthread.php?t=1702465 but it didnt  work as evtouch is no longer available/workable 64bit. But generally their  issue is very much like mine. My system is an Aspire Z3731
 
additionally, is it possible for software to error a usb device like  this (touchscreen is USB) that would be persistent after restart?  
 
thanks

---

