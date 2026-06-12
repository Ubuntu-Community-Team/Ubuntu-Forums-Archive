---
title: "acecad digimemo l2 vs xorg"
date: 2012-05-25
forum: General Help
---

### Post by hgrie on 2012-05-25
Dear World, 

I have the following problem with an Acecad digimemo L2/A602: It's supposed to be workable as an extended input device (or at least as pointer/mouse) under ubuntu 10.04, but it does not so for me: pointer does not react to moving pen. 

I installed the xorg...acecad package. lsmod shows it's present.  I had to meodified an nvidia-xconf generated Xorg.conf by lines: 

Section "InputDevice"
    Identifier     "acecad"
    Driver         "acecad"
    Option         "Device" "auto-dev"
EndSection

Section "ServerLayout"
##### next line uncommented by hgrie
    InputDevice    "acecad" "SendCoreEvents"

[plus more junk]

Xorg.0.log contains: 

(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "acecad"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
[...]
(II) LoadModule: "acecad"
(II) Loading /usr/lib/xorg/modules/input/acecad_drv.so
(II) Module acecad: vendor="X.Org Foundation"
        compiled for 1.7.2, module version = 1.4.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 7.0
[...]
(II) acecad: probing event devices for Acecad tablets
(--) acecad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(--) ACECAD Tablet MaxX:11000 MaxY:8500 MaxZ:0
(==) acecad is in absolute mode
(**) Option "SendCoreEvents"
(**) acecad: always reports core events
(II) XINPUT: Adding extended input device "acecad" (type: TABLET)
(II) acecad Increment: 3
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 2.3.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 7.0
[...]
(EE) acecad: unknown event type/code 4/4
(EE) acecad: unknown event type/code 4/4
(EE) acecad: unknown event type/code 4/4
(EE) acecad: unknown event type/code 4/4

root@james:/home/hgrie# xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; acecad                                      id=6    [slave  pointer  (2)]
&#9116;   &#8627; Dell Premium USB Optical Mouse              id=10    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Dell Dell USB Keyboard                      id=9    [slave  keyboard (3)]

But absolutely no reaction from cursor or in a drawing programme (eg gimp). And yes, the digimemo does what it's supposed to do under the evil operating system. 

New to the forum, so not sure what more info is needed -- sorry.

---

